# Exemplo de Configuração Jira

## 🔧 Como Configurar suas Credenciais Jira

### Passo 1: Encontrar suas Credenciais

#### Account ID
1. Acesse seu Jira
2. Vá em **Settings** > **Account Settings**
3. Copie o **Account ID** (formato: `557058:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`)

#### Project Key
1. Acesse seu projeto no Jira
2. A chave do projeto aparece na URL ou no cabeçalho do projeto
3. Exemplo: se a URL é `https://company.atlassian.net/browse/MYPROJ-123`, a chave é `MYPROJ`

### Passo 2: Configurar no Arquivo de Automação

Edite o arquivo `.ai-engine/automations/jira.md` e substitua:

- `{JIRA_PROJECT_KEY}` → sua chave de projeto (ex: `MYPROJ`)
- `{JIRA_ACCOUNT_ID}` → seu Account ID completo

### Passo 3: Exemplo de Configuração

```markdown
## Configuração do Projeto
- **Project**: MYPROJ
- **Account ID**: 557058:12345678-1234-1234-1234-123456789abc
```

## 🔒 Segurança

**IMPORTANTE**: 
- Nunca commite credenciais reais no repositório
- Use este arquivo apenas como referência
- Mantenha suas credenciais privadas

## 🚨 Troubleshooting

### Erro de Autenticação
- Verifique se o Account ID está correto
- Confirme se você tem permissões no projeto Jira

### Erro de Projeto Não Encontrado
- Verifique se a chave do projeto está correta
- Confirme se o projeto existe e você tem acesso
