# Prompt Gerador de Story

**PAPEL:** Veja `.ai-engine/roles/product-owner.md`

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
Gerar user stories para um epic específico.

## Padrão de Execução
```
execute story-generator based on epic-001-name.md
```

## Entrada
- `product/backlog/epics/epic-XXX-name/epic-XXX-name.md` - Documento específico do epic

## Saída
- `product/backlog/epics/epic-XXX-name/stories/story-001-name/story-001-name.md` - Primeira user story
- `product/backlog/epics/epic-XXX-name/stories/story-002-name/story-002-name.md` - Segunda user story
- Continuar para todas as stories necessárias para o epic

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de gerar qualquer artefato, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente o documento do epic
- [ ] Identificar o escopo e objetivos do epic
- [ ] Planejar decomposição em user stories
- [ ] Definir critérios de aceitação e pontos de história para cada story

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade sobre funcionalidades
- [ ] Formular perguntas específicas sobre:
  - Personas e tipos de usuários envolvidos
  - Fluxos de usuário específicos
  - Regras de negócio detalhadas
  - Critérios de aceitação específicos
  - Estimativas de complexidade

#### 1.3 Apresentação do Plano
- [ ] Apresentar lista de user stories que serão criadas
- [ ] Explicar decomposição e lógica de cada story
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir

**🚨 NÃO GERE NENHUM ARTEFATO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a geração, verificar:
- [ ] Documento do epic existe e é legível
- [ ] Estrutura de pastas do epic existe
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Criação de Checklist
- [ ] Criar `product/backlog/epics/epic-XXX-name/stories/checklist.md` com todas as stories a serem geradas
- [ ] Listar cada story para este epic como não completada `[ ]`
- [ ] Incluir critérios de conclusão para cada story
- [ ] Incluir comando de retomada para novo contexto de AI
- [ ] Atualizar checklist conforme cada story é completada durante a execução

### Passo 4: Execução da Tarefa Principal (apenas após autorização)
1. Ler o documento do epic completamente
2. Usar o template de story de `.ai-engine/templates/story-template.md`
3. **Primeiro, criar a estrutura de pastas das stories:**
   - Criar pasta `product/backlog/epics/epic-XXX-name/stories/` (se não existir)
4. Decompor o epic em user stories:
   - Criar pasta da story: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/`
   - Gerar documento da story: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/story-YYY-name.md`
   - Incluir:
     - ID da Story (formato story-001-name)
     - Formato de user story: "Como um [usuário], eu quero [objetivo] para que [benefício]"
     - Critérios de aceitação (checkboxes)
     - Definição de pronto
     - Estimativa de pontos de história
5. **IMPORTANTE**: Usar numeração globalmente única de story - sem números de story duplicados em todo o projeto
6. **NÃO criar pastas de task ainda** - serão criadas quando geradores de task forem executados

### Passo 5: Operações de Arquivo
- [ ] Criar todas as pastas e arquivos de story conforme especificado
- [ ] Verificar se todos os arquivos foram criados com sucesso

### Passo 6: 🚨 EXECUÇÃO DE AUTOMAÇÃO (CRÍTICO - OBRIGATÓRIO)
**IMEDIATAMENTE após criar arquivos de story, execute TODOS os passos de automação:**

#### 6.1 Integração Jira (OBRIGATÓRIO)
- [ ] Executar automação Jira seguindo `.ai-engine/automations/jira.md`
- [ ] Para cada story gerada:
  - [ ] Tentar criação de Story no Jira com campos básicos (incluindo link do Epic)
  - [ ] Se criação falhar: descobrir campos obrigatórios usando endpoint de metadata
  - [ ] Preencher campos obrigatórios faltantes com padrões apropriados
  - [ ] Tentar novamente criação de Story com conjunto completo de campos
  - [ ] Armazenar Chave da Story usando ferramenta `remember` (se bem-sucedido)
- [ ] Reportar status final de todas as tentativas de criação de story no Jira
- [ ] Continuar execução mesmo se algumas operações do Jira falharem

#### 6.2 Controle de Versão (OBRIGATÓRIO)
- [ ] Executar automação de controle de versão seguindo `.ai-engine/automations/version-control.md`
- [ ] Usar tipo de commit: `docs: generate stories for [epic-name]`
- [ ] Confirmar que git commit foi executado com sucesso
- [ ] Verificar se diretório de trabalho está limpo

### Passo 7: Validação Pós-Execução
Após completar todos os passos, verificar:
- [ ] Todos os arquivos de story criados com sucesso
- [ ] Todas as stories do Jira criadas e chaves armazenadas
- [ ] Git commit executado com mensagem apropriada
- [ ] Instruções do próximo passo fornecidas ao usuário

## Convenção de Nomenclatura
- Pastas de Story: `story-001-name`, `story-002-name`, `story-003-name` (minúsculas, descritivas)
- Arquivos de Story: `story-001-name.md`, `story-002-name.md`, `story-003-name.md`
- **IMPORTANTE**: Usar numeração globalmente única - sem números de story duplicados em todo o projeto

## Referência de Template
Use `.ai-engine/templates/story-template.md` como guia de estrutura.

## ✅ CHECKLIST DE EXECUÇÃO (DEVE COMPLETAR)
Antes de finalizar este prompt, confirme que você:
- [ ] Gerou todos os documentos de story para o epic
- [ ] Criou estrutura de pastas apropriada
- [ ] Executou automação Jira para todas as stories
- [ ] Armazenou todas as chaves de story do Jira
- [ ] Executou automação de controle de versão
- [ ] Forneceu instruções do próximo passo

**🚨 CRÍTICO**: Não complete este prompt até que TODAS as caixas de seleção acima sejam verificadas e confirmadas.

## Próximo Passo
Após gerar documentos de story, execute: `execute backend-tasks-generator based on story-001-name.md`
