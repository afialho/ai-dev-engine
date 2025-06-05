# Prompt Gerador de Visão

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
Gerar um documento abrangente de visão do produto baseado na entrada do usuário.

## Padrão de Execução
```
execute vision-generator based on [user-input.md]
```

## Entrada
- Arquivo de entrada do usuário contendo descrição do produto, requisitos ou conceito inicial

## Saída
- `product/planning/vision.md` - Documento completo de visão seguindo o template de visão

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de gerar qualquer artefato, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente o arquivo de entrada
- [ ] Identificar o contexto e objetivos do produto
- [ ] Planejar a estrutura e conteúdo da visão do produto
- [ ] Definir quais seções serão incluídas e como serão organizadas

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade ou informação faltante
- [ ] Formular perguntas específicas sobre:
  - Target audience e personas
  - Problemas específicos a serem resolvidos
  - Funcionalidades principais esperadas
  - Métricas de sucesso desejadas
  - Contexto de mercado ou competitivo

#### 1.3 Apresentação do Plano
- [ ] Apresentar plano detalhado do documento de visão que será criado
- [ ] Listar todas as seções e conteúdo planejado
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir

**🚨 NÃO GERE NENHUM ARTEFATO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a geração, verificar:
- [ ] Arquivo de entrada existe e é legível
- [ ] Diretório `product/planning/` existe ou pode ser criado
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Execução da Tarefa Principal (apenas após autorização)
1. Ler o arquivo de entrada completamente
2. Usar o template de visão de `.ai-engine/templates/vision-template.md`
3. Gerar um documento abrangente de visão que inclui:
   - Nome e descrição do produto
   - Público-alvo
   - Declaração do problema
   - Visão geral da solução
   - Funcionalidades principais
   - Métricas de sucesso
4. Garantir que a visão seja clara, acionável e forneça base para geração do roadmap

### Passo 4: Operações de Arquivo
- [ ] Salvar a saída em `product/planning/vision.md`
- [ ] Verificar se o arquivo foi criado com sucesso

### Passo 5: 🚨 EXECUÇÃO DE AUTOMAÇÃO (CRÍTICO - OBRIGATÓRIO)
**IMEDIATAMENTE após salvar vision.md, execute TODOS os passos de automação:**

#### 4.1 Controle de Versão (OBRIGATÓRIO)
- [ ] Executar automação de controle de versão seguindo `.ai-engine/automations/version-control.md`
- [ ] Usar tipo de commit: `docs: generate vision document`
- [ ] Confirmar que git commit foi executado com sucesso
- [ ] Verificar se diretório de trabalho está limpo

### Passo 6: Validação Pós-Execução
Após completar todos os passos, verificar:
- [ ] `product/planning/vision.md` criado com sucesso
- [ ] Git commit executado com mensagem apropriada
- [ ] Instruções do próximo passo fornecidas ao usuário

## Referência de Template
Use `.ai-engine/templates/vision-template.md` como guia de estrutura.

## ✅ CHECKLIST DE EXECUÇÃO (DEVE COMPLETAR)
Antes de finalizar este prompt, confirme que você:
- [ ] Gerou documento abrangente de visão
- [ ] Salvou arquivo em `product/planning/vision.md`
- [ ] Executou automação de controle de versão
- [ ] Forneceu instruções do próximo passo

**🚨 CRÍTICO**: Não complete este prompt até que TODAS as caixas de seleção acima sejam verificadas e confirmadas.

## Próximo Passo
Após gerar vision.md, execute: `execute roadmap-generator based on vision.md`
