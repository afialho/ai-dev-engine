# Prompt Gerador de Epic

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
Gerar documentos individuais de epic baseados no roadmap.

## Padrão de Execução
```
execute epic-generator based on roadmap.md
```

## Entrada
- `product/planning/roadmap.md` - Documento completo de roadmap

## Saída
- `product/backlog/epics/epic-001-name/epic-001-name.md` - Primeiro documento de epic
- `product/backlog/epics/epic-002-name/epic-002-name.md` - Segundo documento de epic
- Continuar para todos os epics no roadmap

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de gerar qualquer artefato, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente o roadmap
- [ ] Identificar todos os epics listados no roadmap
- [ ] Planejar a estrutura e conteúdo de cada epic
- [ ] Definir valor de negócio e critérios de aceitação para cada epic

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade sobre escopo dos epics
- [ ] Formular perguntas específicas sobre:
  - Definição detalhada de cada epic
  - Valor de negócio esperado
  - Critérios de sucesso e aceitação
  - Dependências entre epics
  - Priorização relativa dos epics

#### 1.3 Apresentação do Plano
- [ ] Apresentar lista de epics que serão criados
- [ ] Explicar estrutura e conteúdo planejado para cada epic
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir

**🚨 NÃO GERE NENHUM ARTEFATO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a geração, verificar:
- [ ] `product/planning/roadmap.md` existe e é legível
- [ ] Diretório `product/backlog/` existe ou pode ser criado
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Criação de Checklist
- [ ] Criar `product/backlog/epics/checklist.md` com todos os epics a serem gerados
- [ ] Listar cada epic do roadmap como não completado `[ ]`
- [ ] Incluir critérios de conclusão para cada epic
- [ ] Incluir comando de retomada para novo contexto de AI
- [ ] Atualizar checklist conforme cada epic é completado durante a execução

### Passo 4: Execução da Tarefa Principal (apenas após autorização)
1. Ler o documento de roadmap completamente
2. Usar o template de epic de `.ai-engine/templates/epic-template.md`
3. **Primeiro, criar a estrutura de pastas dos epics:**
   - Criar pasta `product/backlog/epics/` (se não existir)
4. Para cada epic no roadmap:
   - Criar pasta do epic: `product/backlog/epics/epic-XXX-name/`
   - Gerar documento do epic: `product/backlog/epics/epic-XXX-name/epic-XXX-name.md`
   - Incluir:
     - ID do Epic (formato epic-001-name)
     - Nome e descrição do epic
     - Valor de negócio
     - Critérios de aceitação
     - Dependências (se houver)
5. Garantir que IDs dos epics usem numeração globalmente única (epic-001, epic-002, etc.)
6. **NÃO criar pasta de stories ainda** - será criada quando story-generator for executado

### Passo 5: Operações de Arquivo
- [ ] Criar todas as pastas e arquivos de epic conforme especificado
- [ ] Verificar se todos os arquivos foram criados com sucesso

### Passo 6: 🚨 EXECUÇÃO DE AUTOMAÇÃO (CRÍTICO - OBRIGATÓRIO)
**IMEDIATAMENTE após criar arquivos de epic, execute TODOS os passos de automação:**

#### 6.1 Integração Jira (OBRIGATÓRIO)
- [ ] Executar automação Jira seguindo `.ai-engine/automations/jira.md`
- [ ] Para cada epic gerado:
  - [ ] Tentar criação de Epic no Jira com campos básicos
  - [ ] Se criação falhar: descobrir campos obrigatórios usando endpoint de metadata
  - [ ] Preencher campos obrigatórios faltantes com padrões apropriados
  - [ ] Tentar novamente criação de Epic com conjunto completo de campos
  - [ ] Armazenar Chave do Epic usando ferramenta `remember` (se bem-sucedido)
- [ ] Reportar status final de todas as tentativas de criação de epic no Jira
- [ ] Continuar execução mesmo se algumas operações do Jira falharem

#### 6.2 Controle de Versão (OBRIGATÓRIO)
- [ ] Executar automação de controle de versão seguindo `.ai-engine/automations/version-control.md`
- [ ] Usar tipo de commit: `docs: generate epic documents`
- [ ] Confirmar que git commit foi executado com sucesso
- [ ] Verificar se diretório de trabalho está limpo

### Passo 7: Validação Pós-Execução
Após completar todos os passos, verificar:
- [ ] Todos os arquivos de epic criados com sucesso
- [ ] Todos os epics do Jira criados e chaves armazenadas
- [ ] Git commit executado com mensagem apropriada
- [ ] Instruções do próximo passo fornecidas ao usuário

## Convenção de Nomenclatura
- Pastas de Epic: `epic-001-name`, `epic-002-name`, `epic-003-name` (minúsculas, descritivas)
- Arquivos de Epic: `epic-001-name.md`, `epic-002-name.md`, `epic-003-name.md`
- **IMPORTANTE**: Usar numeração globalmente única - sem números de epic duplicados em todo o projeto

## Referência de Template
Use `.ai-engine/templates/epic-template.md` como guia de estrutura.

## ✅ CHECKLIST DE EXECUÇÃO (DEVE COMPLETAR)
Antes de finalizar este prompt, confirme que você:
- [ ] Gerou todos os documentos de epic do roadmap
- [ ] Criou estrutura de pastas apropriada
- [ ] Executou automação Jira para todos os epics
- [ ] Armazenou todas as chaves de epic do Jira
- [ ] Executou automação de controle de versão
- [ ] Forneceu instruções do próximo passo

**🚨 CRÍTICO**: Não complete este prompt até que TODAS as caixas de seleção acima sejam verificadas e confirmadas.

## Próximo Passo
Após gerar documentos de epic, execute: `execute story-generator based on epic-001-name.md`
