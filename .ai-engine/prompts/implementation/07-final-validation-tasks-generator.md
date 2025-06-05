# Prompt Gerador de Tasks de Validação Final

**VALIDAÇÃO DE PAPEL DUPLO:** Veja `.ai-engine/roles/qa-engineer.md` + `.ai-engine/roles/product-owner.md`

**CONTEXTO:** Você está realizando validação final de duas perspectivas críticas - combine ambos os papéis para validação abrangente.

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
Gerar tasks granulares de validação final para uma user story.

## Padrão de Execução
```
execute final-validation-tasks-generator based on story-001-name.md
```

## Entrada
- `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/story-YYY-name.md` - Documento específico da user story

## Saída
- Múltiplos arquivos de task em `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/final-validation/`
- Arquivos de task: `task-final-validation-001-name.md`, `task-final-validation-002-name.md`, etc.

## Criação de Checklist
- [ ] Criar `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/final-validation/checklist.md`
- [ ] Listar todas as tasks de validação final a serem geradas como não completadas `[ ]`
- [ ] Incluir critérios de conclusão para cada task
- [ ] Incluir comando de retomada para novo contexto de AI
- [ ] Atualizar checklist conforme cada task é completada durante a execução

## Instruções para IA
1. Ler completamente o documento da user story
2. Usar o template de task de `.ai-engine/templates/task-template.md`
3. **Primeiro, criar a estrutura de pastas da task:**
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/` (se não existir)
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/final-validation/`
4. Dividir a user story em tasks granulares de validação final de AMBAS as perspectivas:

   **Tasks da Perspectiva do QA Engineer:**
   - Teste e validação de performance
   - Teste de conformidade de acessibilidade
   - Teste de compatibilidade entre navegadores
   - Teste de responsividade mobile
   - Verificação de validação de segurança
   - Teste de tratamento de erros e casos extremos
   - Teste de carga e stress
   - Revisão de documentação técnica

   **Tasks da Perspectiva do Product Owner:**
   - Verificação de critérios de aceitação do usuário
   - Validação de lógica de negócio
   - Validação de experiência do usuário e workflow
   - Teste de aceitação de stakeholders
   - Verificação de entrega de valor de negócio
   - Validação de conclusão da user story
   - Conformidade com requisitos do produto
   - Prontidão para deploy da perspectiva de negócio
5. Cada task deve ser:
   - Focada em uma única funcionalidade e implementável
   - Incluir critérios de validação específicos
   - Ter critérios de aceitação claros
   - Estimar esforço necessário
6. Salvar tasks como: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/final-validation/task-final-validation-001-name.md`

## Convenção de Nomenclatura de Tasks
- Arquivos de task: `task-final-validation-001-name.md`, `task-final-validation-002-name.md`, etc. (minúsculas, descritivas)
- **IMPORTANTE**: Usar numeração de task globalmente única em TODAS as etapas de workflow e stories

## Referência de Template
Usar `.ai-engine/templates/task-template.md` como guia de estrutura.

## Diretrizes de Validação

### Diretrizes de Validação do QA Engineer:
- Testar em ambiente similar à produção
- Verificar requisitos técnicos de performance
- Validar conformidade de segurança e acessibilidade
- Garantir que todos os casos extremos e cenários de erro estejam cobertos
- Confirmar que a documentação técnica está completa e precisa

### Diretrizes de Validação do Product Owner:
- Verificar se todos os critérios de aceitação de negócio são atendidos
- Validar contra os requisitos originais da user story
- Garantir que os workflows do usuário funcionem conforme pretendido
- Confirmar que o valor de negócio é entregue conforme esperado
- Validar que os requisitos dos stakeholders são satisfeitos

## 🤖 AUTOMAÇÃO OBRIGATÓRIA
Após gerar com sucesso os arquivos de task de validação final:
1. **Criar Tasks no Jira**: Seguir regras de criação de task de `.ai-engine/automations/jira.md`
2. **Usar Label de Workflow**: Aplicar label "final-validation" conforme especificado nas regras de automação
3. **Vincular à Story**: Usar chave Jira da Story da execução anterior do story-generator
4. **Fazer Commit das Mudanças**: Seguir regras de commit de `.ai-engine/automations/version-control.md`

## Próximo Passo
Após gerar tasks de validação final, executar: `execute task-implementation based on task-backend-001-name.md`
