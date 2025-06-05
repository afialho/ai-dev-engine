# Regras de Automação Jira

## ⚙️ Configuração Necessária

**IMPORTANTE**: Antes de usar esta automação, configure as seguintes variáveis:

- **{JIRA_PROJECT_KEY}**: Substitua pela chave do seu projeto Jira (ex: "MYPROJ")
- **{JIRA_ACCOUNT_ID}**: Substitua pelo seu Account ID do Jira (encontrado em: Jira Settings > Account Settings)

### Como Encontrar seu Account ID:
1. Acesse seu Jira
2. Vá em Settings > Account Settings
3. Copie o Account ID (formato: 557058:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)

## Configuração do Projeto
- **Project**: {JIRA_PROJECT_KEY}
- **Account ID**: {JIRA_ACCOUNT_ID}

## 🚨 TRATAMENTO DINÂMICO DE CAMPOS (CRÍTICO)

### Estratégia de Execução
1. **Tentar Criação**: Tentar criar card do Jira com campos básicos primeiro
2. **Tratar Falhas**: Se criação falhar devido a campos obrigatórios faltantes, descobrir e preenchê-los
3. **Tentar Criação Novamente**: Tentar criação novamente com todos os campos obrigatórios preenchidos
4. **Reportar Sucesso/Falha**: Informar usuário do resultado final

### Mapeamento de Campos Básicos
Começar com estes campos básicos para cada tipo de card:

#### Criação de Epic (Tentativa Inicial)
```json
{
  "fields": {
    "project": {"key": "{JIRA_PROJECT_KEY}"},
    "issuetype": {"name": "Epic"},
    "summary": "[Epic title from generated file]",
    "reporter": {"accountId": "{JIRA_ACCOUNT_ID}"},
    "description": "[Epic description + Augment Code attribution]",
    "labels": ["ai-dev-engine", "epic"]
  }
}
```

#### Criação de Story (Tentativa Inicial)
```json
{
  "fields": {
    "project": {"key": "{JIRA_PROJECT_KEY}"},
    "issuetype": {"name": "Story"},
    "summary": "[Story title from generated file]",
    "description": "[Story description + Augment Code attribution]",
    "parent": {"key": "[Epic Jira key]"},
    "labels": ["ai-dev-engine", "story"]
  }
}
```

#### Criação de Task (Tentativa Inicial)
```json
{
  "fields": {
    "project": {"key": "{JIRA_PROJECT_KEY}"},
    "issuetype": {"name": "Task"},
    "summary": "[Task title from generated file]",
    "parent": {"key": "[Epic Jira key]"},
    "labels": ["ai-dev-engine", "task", "[workflow-stage]"]
  }
}
```

#### Pós-criação de Task: Adicionar Relacionamento com Story
Após criar a Task com sucesso, adicionar descrição e relacionamento:
1. **Atualizar descrição**: PUT /issue/{taskKey} com description
2. **Criar link com Story**: POST /issue/{taskKey}/issuelink com type "Relates" para Story

## 🔄 TRATAMENTO DE ERROS & DESCOBERTA DE CAMPOS

### Passo 1: Tentativa de Criação Inicial
Executar criação de card do Jira com campos básicos acima.

### Passo 2: Tratar Falhas de Criação
Se criação falhar com erro indicando campos obrigatórios faltantes:

1. **Analisar Resposta de Erro**: Extrair informações de campos obrigatórios da mensagem de erro
2. **Descobrir Metadata de Campos**: Usar endpoint `/issue/createmeta/{projectKey}/issuetypes` para obter campos obrigatórios
3. **Preencher Campos Faltantes**: Adicionar valores apropriados para cada campo obrigatório

### Passo 3: Padrões de Campos Obrigatórios Comuns
Se os seguintes campos forem obrigatórios, usar estes padrões:

#### Campo Priority
```json
"priority": {"name": "Medium"}
```

#### Campo Assignee
```json
"assignee": {"accountId": "{JIRA_ACCOUNT_ID}"}
```

#### Campo Reporter
```json
"reporter": {"accountId": "{JIRA_ACCOUNT_ID}"}
```

#### Campo Components (se obrigatório)
```json
"components": [{"name": "AI Development"}]
```

#### Campo Fix Version (se obrigatório)
```json
"fixVersions": [{"name": "Backlog"}]
```

#### Campo Story Points (para Stories)
```json
"customfield_10016": 3
```

#### Campo Epic Name (para Epics)
```json
"customfield_10011": "[Epic title from generated file]"
```

### Passo 4: Tentar Criação Novamente
Após preencher campos obrigatórios, tentar criação de card novamente com conjunto completo de campos.

### Passo 5: Tratamento Final de Erros
Se criação ainda falhar após descoberta e preenchimento de campos:
1. **Registrar Erro Detalhado**: Incluir resposta completa de erro e campos tentados
2. **Continuar Execução**: Não bloquear conclusão do prompt
3. **Notificar Usuário**: Fornecer mensagem de erro clara com próximos passos

## 🔧 FLUXO DE EXECUÇÃO

### Para Cada Criação de Card do Jira:
1. **Tentar Criação Básica**: Usar campos mínimos obrigatórios
2. **Verificar Resposta**:
   - ✅ **Sucesso**: Armazenar chave do card e continuar
   - ❌ **Falha**: Prosseguir para descoberta de campos
3. **Descobrir Campos Obrigatórios**: Consultar endpoint de metadata
4. **Preencher Campos Faltantes**: Adicionar padrões para todos os campos obrigatórios
5. **Tentar Criação Novamente**: Tentar com conjunto completo de campos
6. **Resultado Final**:
   - ✅ **Sucesso**: Armazenar chave do card e continuar
   - ❌ **Falha**: Registrar erro, notificar usuário, continuar execução do prompt

## Labels de Estágio de Workflow
Usar estas labels baseadas no tipo de gerador de task:
- **backend** - Para backend-tasks-generator
- **frontend** - Para frontend-tasks-generator
- **integration** - Para front-back-integration-tasks-generator
- **unit-tests** - Para unit-tests-tasks-generator
- **integration-tests** - Para integration-tests-tasks-generator
- **security** - Para security-validation-tasks-generator
- **final-validation** - Para final-validation-tasks-generator

## Convenções de Nomenclatura
- **Epics**: `epic-001-name`, `epic-002-name` (numeração globalmente única)
- **Stories**: `story-001-name`, `story-002-name` (numeração globalmente única)
- **Tasks**: `task-[workflow]-001-name` (numeração globalmente única em todos os workflows)

## Gerenciamento de Chaves
- **Armazenar Chaves de Epic**: Lembrar chaves de Epic do Jira (ex: PROJ-123) para vincular Stories
- **Armazenar Chaves de Story**: Lembrar chaves de Story do Jira (ex: PROJ-124) para vincular Tasks
- **Usar ferramenta remember**: Armazenar chaves para referência entre prompts

## Formato de Atribuição
Sempre incluir no final das descrições:

```
---
Co-authored by Augment Code (https://www.augmentcode.com/?utm_source=atlassian&utm_medium=jira_issue&utm_campaign=jira)
```

## 🚨 TRATAMENTO APRIMORADO DE ERROS
- **Nunca Bloquear Execução**: Falhas do Jira não devem impedir conclusão do prompt
- **Logging Detalhado**: Registrar todas as tentativas, erros e resultados de descoberta de campos
- **Notificação do Usuário**: Informar claramente o usuário sobre status da automação Jira
- **Degradação Graciosa**: Continuar com geração de arquivos mesmo se Jira falhar
- **Lógica de Retry**: Sempre tentar descoberta de campos e retry antes de desistir

## 💡 EXEMPLO DE IMPLEMENTAÇÃO

### Exemplo: Criação de Epic com Tratamento de Erros

```markdown
## Processo de Criação de Epic no Jira

### Passo 1: Tentativa de Criação Inicial
Tentando criar Epic com campos básicos...

**Chamada API**: POST /rest/api/3/issue
```json
{
  "fields": {
    "project": {"key": "{JIRA_PROJECT_KEY}"},
    "issuetype": {"name": "Epic"},
    "summary": "User Authentication System",
    "reporter": {"accountId": "{JIRA_ACCOUNT_ID}"},
    "description": "Complete user authentication system with login, registration, and password reset functionality.\n\n---\nCo-authored by Augment Code (https://www.augmentcode.com/?utm_source=atlassian&utm_medium=jira_issue&utm_campaign=jira)",
    "labels": ["ai-dev-engine", "epic"]
  }
}
```

### Passo 2: Tratar Falha de Criação (se ocorrer)
❌ **Criação Falhou**: Campos obrigatórios faltantes

**Resposta de Erro**:
```json
{
  "errorMessages": [],
  "errors": {
    "customfield_10011": "Epic Name is required",
    "priority": "Priority is required"
  }
}
```

### Passo 3: Descoberta de Campos
Consultando endpoint de metadata para campos obrigatórios...

**Chamada API**: GET /rest/api/3/issue/createmeta/{JIRA_PROJECT_KEY}/issuetypes

### Passo 4: Preencher Campos Faltantes
Adicionando campos obrigatórios baseados na descoberta:

```json
{
  "fields": {
    "project": {"key": "{JIRA_PROJECT_KEY}"},
    "issuetype": {"name": "Epic"},
    "summary": "User Authentication System",
    "reporter": {"accountId": "{JIRA_ACCOUNT_ID}"},
    "description": "Complete user authentication system...",
    "labels": ["ai-dev-engine", "epic"],
    "customfield_10011": "User Authentication System",
    "priority": {"name": "Medium"}
  }
}
```

### Passo 5: Tentar Criação Novamente
✅ **Criação Bem-sucedida**: Epic criado com chave PROJ-123

**Resultado**: Chave do Epic PROJ-123 armazenada para vincular stories.
```

### Exemplo: Tratamento Gracioso de Falhas

```markdown
## Processo de Criação de Story no Jira

### Passo 1: Tentativa de Criação Inicial
❌ **Criação Falhou**: Campos obrigatórios faltantes

### Passo 2: Descoberta de Campos
❌ **Consulta de Metadata Falhou**: Não foi possível acessar metadata do projeto

### Passo 3: Tentativa Final com Padrões Comuns
❌ **Criação Ainda Falhou**: Problemas de autenticação ou permissão

### Passo 4: Degradação Graciosa
⚠️ **Integração Jira Falhou**: Stories criadas localmente mas não no Jira
- Arquivos locais: ✅ Criados com sucesso
- Cards do Jira: ❌ Falharam devido a [erro específico]
- **Ação Necessária**: Criação manual de cards do Jira ou revisão de permissões
- **Execução do Prompt**: ✅ Continuando com próximos passos
```
