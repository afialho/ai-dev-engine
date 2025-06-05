# Prompt Gerador de Tasks Frontend

**PAPEL:** Veja `.ai-engine/roles/frontend-engineer.md`

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
Gerar tasks granulares de implementação frontend para uma user story.

## Padrão de Execução
```
execute frontend-tasks-generator based on story-001-name.md
```

## Entrada
- `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/story-YYY-name.md` - Documento específico da user story

## Saída
- Múltiplos arquivos de task em `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/frontend/`
- Arquivos de task: `task-frontend-001-name.md`, `task-frontend-002-name.md`, etc.

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de gerar qualquer artefato, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente a user story
- [ ] Identificar todos os componentes frontend necessários
- [ ] Planejar interface e experiência do usuário
- [ ] Definir componentes, páginas e fluxos de navegação

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade sobre UI/UX ou funcionalidades
- [ ] Formular perguntas específicas sobre:
  - Design e layout das interfaces
  - Fluxos de usuário e navegação
  - Componentes reutilizáveis necessários
  - Estados da aplicação e gerenciamento
  - Integrações com APIs backend

#### 1.3 Apresentação do Plano
- [ ] Apresentar lista de tasks frontend que serão criadas
- [ ] Explicar estrutura de componentes e páginas planejadas
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir

**🚨 NÃO GERE NENHUM ARTEFATO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a geração, verificar:
- [ ] Documento da story existe e é legível
- [ ] Estrutura de pastas da story existe
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Criação de Checklist
- [ ] Criar `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/frontend/checklist.md`
- [ ] Listar todas as tasks frontend a serem geradas como não completadas `[ ]`
- [ ] Incluir critérios de conclusão para cada task
- [ ] Incluir comando de retomada para novo contexto de AI
- [ ] Atualizar checklist conforme cada task é completada durante a execução

### Step 4: Primary Task Execution (apenas após autorização)
1. Read the user story document completely
2. Use the task template from `.ai-engine/templates/task-template.md`
3. **First, create the task folder structure:**
   - Create `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/` folder (if it doesn't exist)
   - Create `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/frontend/` folder
4. Break down the user story into granular frontend tasks:
   - UI component creation
   - State management setup
   - API integration
   - Form validation
   - User interaction handling
   - Responsive design implementation
   - Accessibility features
5. Each task should be:
   - Single-focused and implementable
   - Include specific UI/UX details
   - Have clear acceptance criteria
   - Estimate effort required
6. Save tasks as: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/frontend/task-frontend-001-name.md`

### Step 4: File Operations
- [ ] Create all task folders and files as specified
- [ ] Verify all files were created successfully

### Step 5: 🚨 AUTOMATION EXECUTION (CRITICAL - REQUIRED)
**IMMEDIATELY after creating task files, execute ALL automation steps:**

#### 4.1 Jira Integration (MANDATORY)
- [ ] Execute Jira automation following `.ai-engine/automations/jira.md`
- [ ] For each generated task:
  - [ ] Attempt Jira Task creation with basic fields (including Story link and "frontend" label)
  - [ ] If creation fails: discover required fields using metadata endpoint
  - [ ] Populate missing required fields with appropriate defaults
  - [ ] Retry Task creation with complete field set
  - [ ] Confirm task created successfully (if successful)
- [ ] Report final status of all Jira task creation attempts
- [ ] Continue execution even if some Jira operations fail

#### 4.2 Version Control (MANDATORY)
- [ ] Execute version control automation following `.ai-engine/automations/version-control.md`
- [ ] Use commit type: `feat: generate frontend tasks for [story-name]`
- [ ] Confirm git commit executed successfully
- [ ] Verify working directory is clean

### Step 6: Post-Execution Validation
After completing all steps, verify:
- [ ] All task files created successfully
- [ ] All Jira tasks creation attempted with proper error handling
- [ ] Git commit executed with proper message
- [ ] Next step instructions provided to user

## Task Naming Convention
- Task files: `task-frontend-001-name.md`, `task-frontend-002-name.md`, etc. (lowercase, descriptive)
- **IMPORTANT**: Use globally unique task numbering across ALL workflow stages and stories

## Template Reference
Use `.ai-engine/templates/task-template.md` as the structure guide.

## Architecture Reference
Refer to `.ai-engine/architecture/frontend-architecture.md` for technical guidelines.

## ✅ EXECUTION CHECKLIST (MUST COMPLETE)
Before finishing this prompt, confirm you have:
- [ ] Generated all frontend task documents for the story
- [ ] Created proper folder structure
- [ ] Executed Jira automation with error handling for all tasks
- [ ] Applied proper workflow labels
- [ ] Executed version control automation
- [ ] Provided next step instructions

**🚨 CRITICAL**: Do not complete this prompt until ALL checkboxes above are verified and confirmed.

## Next Step
After generating frontend tasks, execute: `execute backend-tasks-generator based on story-001-name.md`
