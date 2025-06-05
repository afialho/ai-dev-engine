# Prompt Gerador de Roadmap

**PAPEL:** Veja `.ai-engine/roles/product-manager.md`

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
Gerar um roadmap do produto com fases e epics baseado no documento de visão.

## Padrão de Execução
```
execute roadmap-generator based on vision.md
```

## Entrada
- `product/planning/vision.md` - Documento completo de visão

## Saída
- `product/planning/roadmap.md` - Roadmap do produto seguindo o template de roadmap

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de gerar qualquer artefato, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente o documento de visão
- [ ] Identificar os objetivos e escopo do produto
- [ ] Planejar a estrutura do roadmap (fases e epics)
- [ ] Definir a progressão lógica do MVP até o produto completo

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade sobre prioridades ou escopo
- [ ] Formular perguntas específicas sobre:
  - Definição do MVP e suas funcionalidades mínimas
  - Critérios para separação entre fases
  - Dependências técnicas ou de negócio
  - Restrições de escopo ou recursos
  - Ordem de prioridade dos epics

#### 1.3 Apresentação do Plano
- [ ] Apresentar estrutura planejada do roadmap (quantas fases, quais epics)
- [ ] Explicar a lógica de progressão entre fases
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir

**🚨 NÃO GERE NENHUM ARTEFATO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a geração, verificar:
- [ ] `product/planning/vision.md` existe e é legível
- [ ] Diretório `product/planning/` existe
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Execução da Tarefa Principal (apenas após autorização)
1. Ler o documento de visão completamente
2. Usar o template de roadmap de `.ai-engine/templates/roadmap-template.md`
3. Gerar um roadmap que inclui:
   - 3-5 fases com progressão clara
   - Fase 1 deve ser MVP (Minimum Viable Product)
   - Cada fase contém apenas epics (ep-001, ep-002, etc.)
   - SEM user stories no roadmap
   - SEM prazos ou estimativas de tempo
   - Progressão clara do MVP até o produto completo
4. Garantir que epics sejam numerados sequencialmente (ep-001, ep-002, etc.)

### Passo 4: Operações de Arquivo
- [ ] Salvar a saída em `product/planning/roadmap.md`
- [ ] Verificar se o arquivo foi criado com sucesso

### Passo 5: 🚨 EXECUÇÃO DE AUTOMAÇÃO (CRÍTICO - OBRIGATÓRIO)
**IMEDIATAMENTE após salvar roadmap.md, execute TODOS os passos de automação:**

#### 5.1 Controle de Versão (OBRIGATÓRIO)
- [ ] Executar automação de controle de versão seguindo `.ai-engine/automations/version-control.md`
- [ ] Usar tipo de commit: `docs: generate roadmap document`
- [ ] Confirmar que git commit foi executado com sucesso
- [ ] Verificar se diretório de trabalho está limpo

### Passo 6: Validação Pós-Execução
Após completar todos os passos, verificar:
- [ ] `product/planning/roadmap.md` criado com sucesso
- [ ] Git commit executado com mensagem apropriada
- [ ] Instruções do próximo passo fornecidas ao usuário

## Requisitos Principais
- SEM prazos ou estimativas de tempo
- Apenas fases e epics
- Separação clara de fases
- Numeração de epics (ep-001, ep-002, etc.)
- Fase 1 = MVP

## Referência de Template
Use `.ai-engine/templates/roadmap-template.md` como guia de estrutura.

## ✅ CHECKLIST DE EXECUÇÃO (DEVE COMPLETAR)
Antes de finalizar este prompt, confirme que você:
- [ ] Gerou documento abrangente de roadmap
- [ ] Salvou arquivo em `product/planning/roadmap.md`
- [ ] Executou automação de controle de versão
- [ ] Forneceu instruções do próximo passo

**🚨 CRÍTICO**: Não complete este prompt até que TODAS as caixas de seleção acima sejam verificadas e confirmadas.

## Próximo Passo
Após gerar roadmap.md, execute: `execute epic-generator based on roadmap.md`
