# AI Dev Engine - Guia do Usuário

## 📖 Visão Geral

O AI Dev Engine é uma ferramenta que automatiza a criação de documentação de produto e tarefas de desenvolvimento usando IA. Este guia explica como usar e personalizar a ferramenta.

## 🎯 Como Funciona

### Fluxo Principal
1. **Entrada**: Você fornece uma descrição do produto
2. **Visão**: IA gera documento de visão do produto
3. **Roadmap**: IA cria roadmap com fases e epics
4. **Epics**: IA detalha cada epic com critérios de aceitação
5. **Stories**: IA quebra epics em user stories
6. **Tasks**: IA gera tarefas técnicas para implementação

### Componentes do Sistema

#### Templates (`.ai-engine/templates/`)
Definem a estrutura dos documentos gerados:
- `vision-template.md` - Estrutura da visão do produto
- `roadmap-template.md` - Formato do roadmap
- `epic-template.md` - Estrutura de épicos
- `story-template.md` - Formato de user stories
- `task-template.md` - Detalhes de tarefas

#### Prompts (`.ai-engine/prompts/`)
Instruções para a IA gerar conteúdo:
- **Planejamento** - Geram visão, roadmap, épicos, stories
- **Implementação** - Geram tarefas técnicas

#### Papéis (`.ai-engine/roles/`)
Personas de IA com expertise específica:
- `product-manager.md` - Product Manager
- `product-owner.md` - Product Owner
- `backend-engineer.md` - Engenheiro Backend
- `frontend-engineer.md` - Engenheiro Frontend
- `qa-engineer.md` - Engenheiro de QA

#### Arquitetura (`.ai-engine/architecture/`)
Padrões técnicos:
- `backend-architecture.md` - Padrões backend
- `frontend-architecture.md` - Padrões frontend

## 🚀 Uso Básico

### Comandos Principais
```bash
# 1. Gerar visão do produto
execute vision-generator based on user-input.md

# 2. Gerar roadmap
execute roadmap-generator based on vision.md

# 3. Gerar épicos
execute epic-generator based on roadmap.md

# 4. Gerar stories para um épico
execute story-generator based on epic-001-name.md

# 5. Gerar tarefas para uma story
execute backend-tasks-generator based on story-001-name.md
execute frontend-tasks-generator based on story-001-name.md
```

### Estrutura de Arquivos Gerados
```
product/
├── planning/
│   ├── vision.md          # Visão do produto
│   └── roadmap.md         # Roadmap com épicos
└── backlog/
    └── epics/
        └── epic-001-name/
            ├── epic-001-name.md     # Documento do épico
            └── stories/
                └── story-001-name/
                    ├── story-001-name.md    # User story
                    └── tasks/
                        ├── backend/         # Tarefas backend
                        ├── frontend/        # Tarefas frontend
                        └── tests/           # Tarefas de teste
```

## 🔧 Personalização

### Modificando Templates
Edite arquivos em `.ai-engine/templates/` para personalizar a estrutura dos documentos:

#### Exemplo: Personalizar Template de Épico
```markdown
# Épico: [Nome do Épico]

## Informações Básicas
**ID:** ep-XXX
**Prioridade:** [Alta/Média/Baixa]
**Estimativa:** [Pontos de história]

## Descrição
[Descrição detalhada do épico]

## Valor de Negócio
[Por que este épico é importante]

## Critérios de Aceitação
- [ ] Critério 1
- [ ] Critério 2
- [ ] Critério 3
```

### Modificando Prompts
Edite arquivos em `.ai-engine/prompts/` para alterar como a IA gera conteúdo:

#### Dicas para Personalização
- Mantenha placeholders claros: `[Descrição]`
- Teste mudanças com exemplos simples
- Documente personalizações importantes
- Mantenha consistência entre templates

## 🔄 Funcionalidade de Pausar/Retomar

### Checklists Automáticos
O sistema cria automaticamente arquivos `checklist.md` durante execuções longas:

#### Localizações dos Checklists:
- **Geração de Épicos**: `product/backlog/epics/checklist.md`
- **Geração de Stories**: `product/backlog/epics/epic-XXX-name/stories/checklist.md`
- **Geração de Tasks**: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/[workflow]/checklist.md`

#### Como Usar:
1. **Durante Execução**: IA cria e atualiza checklists automaticamente
2. **Marcar Progresso**: Mude `[ ]` para `[x]` conforme itens são completados
3. **Retomar Trabalho**: Em nova sessão de IA, diga: "Leia o arquivo checklist.md e continue de onde paramos"

#### Exemplo de Checklist:
```markdown
# Checklist de Geração de Épicos

## Tarefa Atual: Geração de Épicos
**Comando para Retomar:** `execute epic-generator based on roadmap.md`

## Épicos para Gerar:
- [x] epic-001-user-authentication
- [ ] epic-002-product-catalog
- [ ] epic-003-shopping-cart

## Instruções:
Marque cada épico como concluído `[x]` quando:
1. Pasta do épico criada
2. Documento do épico gerado
3. Card do Jira criado
4. Commit Git executado
```

## 🏗️ Personalização de Arquitetura

### Configuração de Stack Tecnológico
Modificar arquivos de arquitetura para corresponder às suas escolhas tecnológicas:

#### Exemplo de Arquitetura Backend
```markdown
## Stack de Tecnologia
### Tecnologias Principais
- **Runtime:** Python 3.11+
- **Framework:** FastAPI
- **Banco de Dados:** PostgreSQL + Redis
- **Autenticação:** Auth0
- **Estilo de API:** GraphQL com fallback REST

### Padrões Personalizados
- Todas as APIs devem incluir rate limiting
- Consultas de banco de dados devem usar connection pooling
- Respostas de erro devem incluir IDs de correlação
```

### Melhores Práticas de Arquitetura
- Definir versões específicas de tecnologia
- Incluir requisitos de segurança
- Especificar padrões de performance
- Documentar requisitos de deploy

## 📊 Padrões de Workflow Avançados

### Projetos Multi-Equipe
Para projetos maiores com múltiplas equipes:

#### 1. Atribuição de Equipe Baseada em Épico
```bash
# Equipe A: Autenticação e Gerenciamento de Usuário
execute story-generator based on epic-001-name.md

# Equipe B: Catálogo de Produtos
execute story-generator based on epic-002-name.md

# Equipe C: Processamento de Pagamento
execute story-generator based on epic-003-name.md
```

#### 2. Geração Paralela de Tasks
```bash
# Gerar todos os tipos de task para uma story
execute frontend-tasks-generator based on story-001-name.md &
execute backend-tasks-generator based on story-001-name.md &
execute unit-tests-tasks-generator based on story-001-name.md &
wait
```

### Desenvolvimento Iterativo
Para desenvolvimento ágil/iterativo:

#### 1. Abordagem MVP-First
```bash
# Focar primeiro nos épicos MVP
execute story-generator based on epic-001-name.md  # Funcionalidades principais
execute story-generator based on epic-002-name.md  # Funcionalidades essenciais
# Pular épicos avançados inicialmente
```

#### 2. Refinamento de Story
```bash
# Regenerar stories conforme requisitos evoluem
execute story-generator based on epic-001-name.md  # Requisitos atualizados
```

## 🔍 Garantia de Qualidade

### Estratégias de Validação

#### 1. Verificações de Qualidade de Conteúdo
Antes de prosseguir para implementação:
- Verificar se todos os critérios de aceitação são testáveis
- Garantir que o valor de negócio está claramente definido
- Verificar se as dependências estão identificadas
- Validar se as estimativas de story points são razoáveis

#### 2. Verificações de Qualidade Técnica
Antes da implementação de código:
- Revisar decisões de arquitetura
- Validar escolhas tecnológicas
- Garantir que requisitos de segurança estão incluídos
- Verificar se requisitos de performance estão definidos

### Testando Conteúdo Gerado
```bash
# Teste o fluxo completo com um projeto simples
mkdir test-project && cd test-project

# Crie entrada mínima
echo "# Produto de Teste: App de Todo Simples" > user-input.md

# Execute o fluxo completo
execute vision-generator based on user-input.md
execute roadmap-generator based on vision.md
execute epic-generator based on roadmap.md
execute story-generator based on epic-001-name.md
execute readiness-check
```

## 🔄 Funcionalidade de Pausar/Retomar

### Criação Automática de Checklist
O AI Dev Engine cria automaticamente arquivos `checklist.md` durante a execução de prompts multi-task:

#### Localizações de Checklist:
- **Geração de Épico**: `product/backlog/epics/checklist.md`
- **Geração de Story**: `product/backlog/epics/epic-XXX-name/stories/checklist.md`
- **Geração de Task**: `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/[workflow]/checklist.md`

#### Como Usar:
1. **Durante Execução**: IA cria e atualiza checklists automaticamente
2. **Marcar Progresso**: Atualizar `[ ]` para `[x]` conforme itens são completados
3. **Retomar Trabalho**: Em nova sessão de IA, dizer: "Leia o arquivo checklist.md e continue de onde paramos"
4. **Entre Sessões**: Funciona entre diferentes contextos e sessões de IA

#### Exemplo de Checklist:
```markdown
# Checklist de Geração de Épicos

## Tarefa Atual: Geração de Épicos
**Comando para Retomar:** `execute epic-generator based on roadmap.md`

## Épicos para Gerar:
- [x] epic-001-user-authentication
- [ ] epic-002-product-catalog
- [ ] epic-003-shopping-cart

## Instruções:
Marque cada épico como concluído `[x]` quando:
1. Pasta do épico criada
2. Documento do épico gerado
3. Card épico do Jira criado
4. Commit Git executado

## Como Continuar:
**Se geração de épico incompleta:** Execute novamente `execute epic-generator based on roadmap.md`

## Contexto para Nova IA:
- Projeto: Plataforma E-commerce
- Fase: Geração de Épicos
- Concluído: epic-001-user-authentication
- Próximo: Continuar com épicos restantes
```

## 🚀 Otimização de Performance

### Estratégias para Projetos Grandes

#### 1. Geração Incremental
Para projetos com muitos épicos:
```bash
# Gerar épicos incrementalmente
execute epic-generator based on roadmap.md  # Gera todos os épicos
# Então processar um épico por vez
execute story-generator based on epic-001-name.md
# Completar implementação do epic-001 antes de mover para epic-002
```

#### 2. Geração Seletiva de Tasks
Gerar apenas tipos de task necessários:
```bash
# Para mudanças apenas de frontend
execute frontend-tasks-generator based on story-001-name.md
execute unit-tests-tasks-generator based on story-001-name.md
# Pular tasks de backend se não necessárias
```

### Gerenciamento de Recursos
- Processar uma user story completamente antes de iniciar a próxima
- Usar readiness-check frequentemente para detectar problemas cedo
- Manter arquivos gerados organizados e limpar artefatos não utilizados

## 🔧 Integração com Ferramentas Externas

### Integrações Automatizadas
O AI Dev Engine inclui automações integradas que executam automaticamente:

#### Integração Jira (Automática)
- **Geração de Épico**: Cria cards de Épico no seu projeto Jira configurado
- **Geração de Story**: Cria cards de Story vinculados ao Épico
- **Geração de Task**: Cria cards de Task vinculados à Story com labels de workflow
- **Rastreamento de Workflow**: Tasks marcadas por estágio (`backend`, `frontend`, `integration`, etc.)

**Nota**: Configure suas credenciais Jira em `.ai-engine/automations/jira.md` antes de usar.

#### Integração de Controle de Versão (Automática)
- **Commits Automáticos**: Cria commits convencionais após mudanças de arquivo
- **Tipos de Commit**: Usa `feat`, `docs`, `test` baseado no tipo de prompt
- **Push Manual**: Usuário controla quando fazer push para remoto

#### Integração Manual de Controle de Versão
```bash
# Commits manuais para mudanças adicionais
git add product/planning/
git commit -m "docs: atualizar visão e roadmap do produto"

git add product/backlog/epics/epic-001-name/
git commit -m "docs: gerar épico epic-001-name com user stories"
```

### Integração de Gerenciamento de Projeto
- Criação automática de cards Jira com hierarquia adequada
- IDs de Story como referências de ticket
- Critérios de aceitação mapeados para descrições do Jira

### Integração CI/CD
```bash
# Validar estrutura do projeto no CI
if ! execute readiness-check; then
  echo "Projeto não está pronto para implementação"
  exit 1
fi
```

## 📋 Melhores Práticas

### Organização de Projeto
1. **Começar Pequeno** - Iniciar com um projeto simples para aprender o workflow
2. **Iterar Frequentemente** - Usar readiness-check frequentemente para detectar problemas cedo
3. **Documentar Decisões** - Manter notas sobre personalizações e por que foram feitas
4. **Versionar Templates** - Rastrear mudanças em templates e prompts

### Colaboração em Equipe
1. **Templates Compartilhados** - Garantir que todos os membros da equipe usem os mesmos templates
2. **Propriedade Clara** - Atribuir propriedade de épico/story claramente
3. **Revisões Regulares** - Revisar conteúdo gerado antes da implementação
4. **Compartilhamento de Conhecimento** - Documentar personalizações específicas da equipe

### Manutenção
1. **Atualizações Regulares** - Manter templates e prompts atualizados com necessidades da equipe
2. **Loop de Feedback** - Coletar feedback de desenvolvedores usando tasks geradas
3. **Melhoria Contínua** - Refinar prompts baseado na qualidade da saída
4. **Documentação** - Manter este guia do usuário atualizado com novos padrões

## 🚨 Solução de Problemas Avançados

### Problemas de Template
- **Problema:** Conteúdo gerado não corresponde às expectativas
- **Solução:** Revisar e personalizar templates em `.ai-engine/templates/`

### Problemas de Prompt
- **Problema:** IA gera conteúdo incorreto ou incompleto
- **Solução:** Refinar prompts em `.ai-engine/prompts/` com instruções mais específicas

### Problemas de Papel
- **Problema:** Conteúdo gerado não corresponde ao nível de expertise esperado
- **Solução:** Personalizar papéis em `.ai-engine/roles/` para corresponder aos requisitos do seu domínio

### Problemas de Arquitetura
- **Problema:** Código gerado não segue padrões da equipe
- **Solução:** Atualizar diretrizes de arquitetura em `.ai-engine/architecture/`

### Problemas de Workflow
- **Problema:** Processo não se adequa ao workflow da equipe
- **Solução:** Personalizar prompts e criar padrões de execução específicos da equipe

## 📞 Suporte Avançado

Para personalizações complexas ou questões de integração:
1. Revisar a estrutura completa da base de código
2. Examinar templates existentes para padrões
3. Testar personalizações com exemplos simples primeiro
4. Documentar padrões bem-sucedidos para reutilização da equipe

---
**Guia de Uso Avançado** - AI Dev Engine v1.0
