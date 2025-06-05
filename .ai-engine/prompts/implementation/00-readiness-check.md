# Prompt de Verificação de Prontidão

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
Verificar se o projeto está pronto para iniciar a fase de implementação checando todos os pré-requisitos necessários.

## Padrão de Execução
```
execute readiness-check
```

**Nota:** Este é o único prompt que não requer o padrão "based on [file.md]", pois valida a estrutura atual do projeto.

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: Validação de Pré-requisitos
Este prompt deve verificar os seguintes requisitos antes que a implementação possa começar:

#### 1.1 Validação de Arquitetura
- [ ] `.ai-engine/architecture/backend-architecture.md` existe e contém conteúdo substancial
- [ ] `.ai-engine/architecture/frontend-architecture.md` existe e contém conteúdo substancial
- [ ] Arquivos de arquitetura definem tecnologias específicas, padrões e normas

#### 1.2 Validação de Planejamento
- [ ] `product/planning/vision.md` existe e contém visão do produto
- [ ] `product/planning/roadmap.md` existe e contém roadmap com fases e épicos

#### 1.3 Validação de Backlog
- [ ] Pelo menos um épico existe em `product/backlog/epics/` (ex: `epic-001-name/`)
- [ ] Pelo menos uma story existe dentro de qualquer épico (ex: `epic-001-name/stories/story-001-name/`)
- [ ] Arquivos de épico e story contêm conteúdo real (não apenas templates)

### Step 2: Primary Task Execution
1. **Check Architecture Files:**
   - Verify both backend and frontend architecture files exist
   - Ensure files contain more than just template content
   - Validate that technologies and patterns are specified

2. **Check Planning Files:**
   - Verify vision.md exists and contains product information
   - Verify roadmap.md exists and contains phases with epics

3. **Check Backlog Structure:**
   - Look for at least one epic folder (epic-001-name, epic-002-name, etc.)
   - Look for at least one story folder within any epic
   - Verify epic and story files contain actual content

4. **Generate Validation Report:**
   - If ALL requirements are met: Generate SUCCESS report
   - If ANY requirement is missing: Generate FAILURE report with details

### Step 3: Report Generation
- [ ] Generate comprehensive validation report
- [ ] Provide clear next steps based on validation results

### Step 4: 🚨 AUTOMATION EXECUTION (CRITICAL - REQUIRED)
**IMMEDIATELY after generating validation report, execute ALL automation steps:**

#### 4.1 Version Control (MANDATORY)
- [ ] Execute version control automation following `.ai-engine/automations/version-control.md`
- [ ] Use commit type: `docs: execute readiness check validation`
- [ ] Confirm git commit executed successfully
- [ ] Verify working directory is clean

### Step 5: Post-Execution Validation
After completing all steps, verify:
- [ ] Validation report generated successfully
- [ ] Git commit executed with proper message
- [ ] Clear next step instructions provided to user

## Success Output Format
```markdown
# ✅ READINESS CHECK: PASSED

## Project Ready for Implementation!

### ✅ Architecture Validated:
- Backend architecture defined: [technology stack found]
- Frontend architecture defined: [technology stack found]

### ✅ Planning Validated:
- Product vision defined
- Roadmap with [X] phases and [Y] epics

### ✅ Backlog Validated:
- [X] epics found
- [Y] stories found
- Ready for task generation

## Next Steps:
1. Execute: `execute backend-tasks-generator based on story-001-name.md`
2. Continue with implementation workflow
```

## Failure Output Format
```markdown
# ❌ READINESS CHECK: FAILED

## Missing Prerequisites:

### ❌ Architecture Issues:
- [ ] Backend architecture missing/incomplete
- [ ] Frontend architecture missing/incomplete

### ❌ Planning Issues:
- [ ] Vision document missing
- [ ] Roadmap document missing

### ❌ Backlog Issues:
- [ ] No epics found
- [ ] No stories found

## Required Actions:
1. [Specific action needed]
2. [Specific action needed]
3. Run readiness-check again after completing requirements

## Commands to Execute:
- `execute vision-generator based on user-input.md`
- `execute roadmap-generator based on vision.md`
- `execute epic-generator based on roadmap.md`
- `execute story-generator based on epic-001-name.md`
```

## Validation Guidelines
- Architecture files must contain specific technology choices, not just generic templates
- Planning files must contain actual product information, not placeholder text
- At least one complete epic-story chain must exist before implementation
- All file paths must follow the established naming conventions

## ✅ EXECUTION CHECKLIST (MUST COMPLETE)
Before finishing this prompt, confirm you have:
- [ ] Validated all architecture files
- [ ] Validated all planning files
- [ ] Validated backlog structure
- [ ] Generated comprehensive validation report
- [ ] Executed version control automation
- [ ] Provided clear next step instructions

**🚨 CRITICAL**: Do not complete this prompt until ALL checkboxes above are verified and confirmed.

## Next Step
If readiness check passes, execute: `execute backend-tasks-generator based on story-001-name.md`
