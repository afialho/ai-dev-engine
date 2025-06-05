# Prompt Gerador de Tasks de Validação de Segurança

**PAPEL:** Veja `.ai-engine/roles/security-engineer.md`

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
Gerar tasks granulares de validação de segurança para uma user story.

## Padrão de Execução
```
execute security-validation-tasks-generator based on story-001-name.md
```

## Entrada
- `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/story-YYY-name.md` - Documento específico da user story

## Saída
- Múltiplos arquivos de task em `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/security-validation/`
- Arquivos de task: `task-security-001-name.md`, `task-security-002-name.md`, etc.

## Criação de Checklist
- [ ] Criar `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/security-validation/checklist.md`
- [ ] Listar todas as tasks de validação de segurança a serem geradas como não completadas `[ ]`
- [ ] Incluir critérios de conclusão para cada task
- [ ] Incluir comando de retomada para novo contexto de AI
- [ ] Atualizar checklist conforme cada task é completada durante a execução

## Instruções para IA
1. Ler completamente o documento da user story
2. Usar o template de task de `.ai-engine/templates/task-template.md`
3. **Primeiro, criar a estrutura de pastas da task:**
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/` (se não existir)
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/security-validation/`
4. Dividir a user story em tasks granulares de validação de segurança:
   - Validação e sanitização de entrada
   - Verificações de autenticação e autorização
   - Prevenção de injeção SQL
   - Prevenção de Cross-Site Scripting (XSS)
   - Proteção contra Cross-Site Request Forgery (CSRF)
   - Validação de criptografia de dados
   - Verificação de controle de acesso
   - Validação de cabeçalhos de segurança
5. Cada task deve ser:
   - Focada em uma única funcionalidade e implementável
   - Incluir cenários de segurança específicos
   - Ter critérios de aceitação claros
   - Estimar esforço necessário
6. Salvar tasks como: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/security-validation/task-security-001-name.md`

## Convenção de Nomenclatura de Tasks
- Arquivos de task: `task-security-001-name.md`, `task-security-002-name.md`, etc. (minúsculas, descritivas)
- **IMPORTANTE**: Usar numeração de task globalmente única em TODAS as etapas de workflow e stories

## Referência de Template
Usar `.ai-engine/templates/task-template.md` como guia de estrutura.

## Diretrizes de Segurança
- Seguir os 10 principais riscos de segurança do OWASP
- Implementar defesa em profundidade
- Validar todas as entradas e saídas
- Usar práticas de codificação segura

## 🤖 AUTOMAÇÃO OBRIGATÓRIA
Após gerar com sucesso os arquivos de task de validação de segurança:
1. **Criar Tasks no Jira**: Seguir regras de criação de task de `.ai-engine/automations/jira.md`
2. **Usar Label de Workflow**: Aplicar label "security" conforme especificado nas regras de automação
3. **Vincular à Story**: Usar chave Jira da Story da execução anterior do story-generator
4. **Fazer Commit das Mudanças**: Seguir regras de commit de `.ai-engine/automations/version-control.md`

## Próximo Passo
Após gerar tasks de validação de segurança, executar: `execute final-validation-tasks-generator based on story-001-name.md`
