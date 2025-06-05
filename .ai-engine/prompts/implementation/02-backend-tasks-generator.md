# Prompt Gerador de Tasks Backend

**PAPEL:** Veja `.ai-engine/roles/backend-engineer.md`

---

## 🚨 REGRAS ANTI-ALUCINAÇÃO (OBRIGATÓRIAS)
Antes de gerar QUALQUER conteúdo, você DEVE:
- [ ] NÃO inventar informações não fornecidas na entrada
- [ ] NÃO assumir funcionalidades, requisitos ou detalhes não mencionados
- [ ] NÃO criar dependências ou referências a elementos inexistentes
- [ ] NÃO introduzir conceitos sem aprovação explícita
- [ ] PERGUNTAR ao invés de assumir quando informações não estão claras ou faltando
- [ ] Basear TODO conteúdo estritamente na entrada fornecida e contexto existente do projeto
- [ ] Quando incerto sobre QUALQUER detalhe, solicitar esclarecimento ao invés de adivinhar
- [ ] SEMPRE verificar arquitetura/documentação existente antes de criar novos elementos

### Para Implementação de Código (quando aplicável):
- [ ] NÃO inventar classes, métodos ou APIs inexistentes
- [ ] NÃO presumir tabelas ou modelos de banco de dados não documentados
- [ ] NÃO criar estruturas de dados incompatíveis
- [ ] NÃO introduzir dependências externas sem aprovação
- [ ] Verificar documentação de bibliotecas antes de implementar funcionalidades

## Propósito
Gerar tasks granulares de implementação backend para uma user story.

## Padrão de Execução
```
execute backend-tasks-generator based on story-001-name.md
```

## Entrada
- `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/story-YYY-name.md` - Documento específico da user story

## Saída
- Múltiplos arquivos de task em `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/backend/`
- Arquivos de task: `task-backend-001-name.md`, `task-backend-002-name.md`, etc.

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de gerar qualquer artefato, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente a user story
- [ ] Identificar todos os componentes backend necessários
- [ ] Planejar arquitetura e estrutura técnica
- [ ] Definir endpoints, modelos e serviços necessários

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade técnica ou de negócio
- [ ] Formular perguntas específicas sobre:
  - Estrutura de dados e modelos
  - Endpoints de API necessários
  - Regras de validação e negócio
  - Integrações com sistemas externos
  - Requisitos de performance e segurança

#### 1.3 Apresentação do Plano
- [ ] Apresentar lista de tasks backend que serão criadas
- [ ] Explicar arquitetura e componentes técnicos planejados
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir

**🚨 NÃO GERE NENHUM ARTEFATO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a geração, verificar:
- [ ] Documento da story existe e é legível
- [ ] Estrutura de pastas da story existe
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Criação de Checklist
- [ ] Criar `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/backend/checklist.md`
- [ ] Listar todas as tasks backend a serem geradas como não completadas `[ ]`
- [ ] Incluir critérios de conclusão para cada task
- [ ] Incluir comando de retomada para novo contexto de AI
- [ ] Atualizar checklist conforme cada task é completada durante a execução

### Passo 4: Execução Principal da Task (apenas após autorização)
1. Ler completamente o documento da user story
2. Usar o template de task de `.ai-engine/templates/task-template.md`
3. **Primeiro, criar a estrutura de pastas da task:**
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/` (se não existir)
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/backend/`
4. Dividir a user story em tasks granulares de backend:
   - Design de schema de banco de dados
   - Criação de endpoints de API
   - Implementação de lógica de negócio
   - Validação de dados
   - Tratamento de erros
   - Autenticação/autorização (se necessário)
5. Cada task deve ser:
   - Focada em uma única funcionalidade e implementável
   - Incluir detalhes técnicos específicos
   - Ter critérios de aceitação claros
   - Estimar esforço necessário
6. Salvar tasks como: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/backend/task-backend-001-name.md`

### Passo 5: Operações de Arquivo
- [ ] Criar todas as pastas e arquivos de task conforme especificado
- [ ] Verificar se todos os arquivos foram criados com sucesso

### Passo 6: 🚨 EXECUÇÃO DE AUTOMAÇÃO (CRÍTICO - OBRIGATÓRIO)
**IMEDIATAMENTE após criar os arquivos de task, executar TODOS os passos de automação:**

#### 6.1 Integração Jira (OBRIGATÓRIA)
- [ ] Executar automação Jira seguindo `.ai-engine/automations/jira.md`
- [ ] Para cada task gerada:
  - [ ] Tentar criação de Task no Jira com campos básicos (incluindo link da Story e label "backend")
  - [ ] Se criação falhar: descobrir campos obrigatórios usando endpoint de metadata
  - [ ] Preencher campos obrigatórios faltantes com valores padrão apropriados
  - [ ] Tentar novamente criação de Task com conjunto completo de campos
  - [ ] Confirmar task criada com sucesso (se bem-sucedida)
- [ ] Reportar status final de todas as tentativas de criação de tasks no Jira
- [ ] Continuar execução mesmo se algumas operações do Jira falharem

#### 6.2 Controle de Versão (OBRIGATÓRIO)
- [ ] Executar automação de controle de versão seguindo `.ai-engine/automations/version-control.md`
- [ ] Usar tipo de commit: `feat: generate backend tasks for [story-name]`
- [ ] Confirmar commit git executado com sucesso
- [ ] Verificar se diretório de trabalho está limpo

### Passo 7: Validação Pós-Execução
Após completar todos os passos, verificar:
- [ ] Todos os arquivos de task criados com sucesso
- [ ] Todas as tasks do Jira criadas com labels apropriadas
- [ ] Commit git executado com mensagem apropriada
- [ ] Instruções de próximo passo fornecidas ao usuário

## Convenção de Nomenclatura de Tasks
- Arquivos de task: `task-backend-001-name.md`, `task-backend-002-name.md`, etc. (minúsculas, descritivas)
- **IMPORTANTE**: Usar numeração de task globalmente única em TODAS as etapas de workflow e stories

## Referência de Template
Usar `.ai-engine/templates/task-template.md` como guia de estrutura.

## Referência de Arquitetura
Consultar `.ai-engine/architecture/backend-architecture.md` para diretrizes técnicas.

## ✅ CHECKLIST DE EXECUÇÃO (DEVE COMPLETAR)
Antes de finalizar este prompt, confirmar que você:
- [ ] Gerou todos os documentos de task backend para a story
- [ ] Criou estrutura de pastas apropriada
- [ ] Executou automação Jira para todas as tasks
- [ ] Aplicou labels de workflow apropriadas
- [ ] Executou automação de controle de versão
- [ ] Forneceu instruções de próximo passo

**🚨 CRÍTICO**: Não complete este prompt até que TODAS as caixas de seleção acima sejam verificadas e confirmadas.

## Próximo Passo
Após gerar tasks backend, executar: `execute front-back-integration-tasks-generator based on story-001-name.md`
