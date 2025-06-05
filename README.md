# AI Dev Engine

## 🎯 Visão Geral
O AI Dev Engine é um motor de desenvolvimento de software alimentado por IA que transforma ideias de produtos em código pronto para produção através de um fluxo de trabalho estruturado e sistemático.

### **Fluxo de Desenvolvimento Completo:**
1. **📋 Fase de Planejamento** - Visão → Roadmap → Épicos → User Stories
2. **✅ Fase de Validação** - Verificação de prontidão e validação de arquitetura
3. **🔧 Fase de Implementação** - Frontend → Backend → Integração → Testes → Segurança → Validação Final
4. **💻 Geração de Código** - Implementação automatizada de tarefas em código real

### **Principais Benefícios do Fluxo:**
- **Abordagem Sistemática** - Nenhum passo perdido ou requisito esquecido
- **Divisão Granular de Tarefas** - Cada funcionalidade se torna tarefas implementáveis
- **Garantia de Qualidade** - Testes e validação de segurança integrados
- **Consistência de Arquitetura** - Segue padrões técnicos definidos
- **AI-First** - Desenvolvimento completo com IA e documentação em cada passo

Todo o fluxo é **revisado e guiado por personas de IA de nível sênior**: Senior Product Manager, Senior Product Owner, Senior Backend Engineer, Senior Frontend Engineer, Senior Full-Stack Engineer, Senior QA Engineer e Senior Security Engineer - garantindo qualidade de nível empresarial e melhores práticas durante todo o processo de desenvolvimento.

## 🚀 Início Rápido

### Pré-requisitos
- Assistente de IA com acesso ao codebase
- Entendimento do padrão de execução de prompts

### Prompts Essenciais
```bash
# Fase de Planejamento
execute vision-generator based on product-idea.md
execute roadmap-generator based on vision.md
execute epic-generator based on roadmap.md
execute story-generator based on epic-001-name.md

# Fase de Implementação
execute readiness-check
execute frontend-tasks-generator based on story-001-name.md
execute task-implementation based on task-frontend-001-name.md
```

## 📁 Estrutura do Projeto
```
ai-dev-engine/
├── product-idea.md          # 📝 Sua ideia de produto (comece aqui!)
├── README.md                # Documentação do projeto
├── .ai-engine/              # Arquivos centrais do AI engine (ocultos)
│   ├── prompts/             # Prompts de IA para geração
│   ├── templates/           # Templates de documentos
│   ├── roles/               # Definições de papéis para personas de IA
│   ├── architecture/        # Diretrizes técnicas
│   └── automations/         # Regras de automação (Jira, Git, etc.)
├── docs/                    # Documentação adicional
├── product/                 # Artefatos de produto gerados
│   ├── planning/            # Visão e roadmap
│   └── backlog/             # Épicos e stories
└── infrastructure/          # Código gerado
    ├── backend/             # Implementação backend
    └── frontend/            # Implementação frontend
```

## 🔄 Tutorial Completo do Fluxo

### Projeto de Exemplo: Plataforma E-commerce
Vamos percorrer a construção de uma plataforma e-commerce da ideia à implementação.

## Passo 1: Criar Ideia do Produto
Criar `product-idea.md`:
```markdown
# Ideia do Produto: Marketplace de Artesãos
- Marketplace online para artesanato feito à mão
- Público-alvo: Artesãos independentes e clientes
- Funcionalidades: listagens de produtos, carrinho de compras, pagamentos
- Plataforma: Aplicação web com React + Node.js
```

## Passo 2: Gerar Documento de Visão
**Prompt:** `execute vision-generator based on product-idea.md`
**Output:** `product/planning/vision.md`

Cria visão abrangente com público-alvo, declaração do problema, visão geral da solução e métricas de sucesso.

## Passo 3: Criar Roadmap do Produto
**Prompt:** `execute roadmap-generator based on vision.md`
**Output:** `product/planning/roadmap.md`

Gera roadmap com 3-5 fases, começando com MVP. Sem prazos, apenas progressão lógica.

## Passo 4: Gerar Documentos de Épicos
**Prompt:** `execute epic-generator based on roadmap.md`
**Output:** `product/backlog/epics/epic-001-name/epic-001-name.md`, `epic-002-name/epic-002-name.md`, etc.

Cria documentos individuais de épicos com valor de negócio, critérios de aceitação e dependências.

## Passo 5: Criar User Stories
**Prompt:** `execute story-generator based on epic-001-name.md`
**Output:** `product/backlog/epics/epic-001-name/stories/story-001-name/story-001-name.md`, etc.

Divide épicos em user stories implementáveis com critérios de aceitação e story points.

## Passo 6: Verificar Prontidão para Implementação
**Prompt:** `execute readiness-check`

Valida que:
- ✅ Arquiteturas backend e frontend estão definidas
- ✅ Visão e roadmap existem
- ✅ Pelo menos um épico e story existem
- ✅ Todos os arquivos contêm conteúdo real

**Output de Sucesso:**
```markdown
# ✅ VERIFICAÇÃO DE PRONTIDÃO: APROVADA
## Projeto Pronto para Implementação!
### ✅ Arquitetura Validada:
- Arquitetura backend definida: Node.js com Express
- Arquitetura frontend definida: React com TypeScript
### ✅ Planejamento Validado:
- Visão do produto definida
- Roadmap com 3 fases e 5 épicos
### ✅ Backlog Validado:
- 2 épicos encontrados, 4 stories encontradas
- Pronto para geração de tarefas
```

## Passo 7: Gerar Tarefas de Implementação
Execute os geradores de tarefas:

```bash
# Tarefas de Frontend
execute frontend-tasks-generator based on story-001-name.md

# Tarefas de Backend
execute backend-tasks-generator based on story-001-name.md

# Tarefas de Integração
execute front-back-integration-tasks-generator based on story-001-name.md

# Tarefas de Testes
execute unit-tests-tasks-generator based on story-001-name.md
execute integration-tests-tasks-generator based on story-001-name.md

# Validação de Segurança
execute security-validation-tasks-generator based on story-001-name.md
execute final-validation-tasks-generator based on story-001-name.md
```

## Passo 8: Implementar Código
```bash
execute task-implementation based on task-frontend-001-name.md
```

Converte tarefas em código real nos diretórios `infrastructure/backend/` ou `infrastructure/frontend/`.

## 📋 Referência de Prompts

### Prompts de Planejamento
```bash
execute vision-generator based on product-idea.md      # Gera visão do produto
execute roadmap-generator based on vision.md           # Cria roadmap
execute epic-generator based on roadmap.md             # Gera épicos
execute story-generator based on epic-001-name.md      # Cria user stories
```

### Prompts de Implementação
```bash
execute readiness-check                                 # Valida prontidão
execute frontend-tasks-generator based on story-001-name.md
execute backend-tasks-generator based on story-001-name.md
execute task-implementation based on task-frontend-001-name.md
```

### Convenções de Nomenclatura
- **Épicos:** `epic-001-name`, `epic-002-name` (minúsculo, descritivo)
- **Stories:** `story-001-name`, `story-002-name` (minúsculo, descritivo)
- **Tarefas:** `task-frontend-001-name`, `task-backend-002-name` (minúsculo, descritivo)
- **Arquivos:** Formato `.md` para documentação
- **Numeração única:** Todos os números são únicos globalmente no projeto

## 🚨 Solução de Problemas

### Problemas Comuns
| Problema | Causa | Solução |
|----------|-------|---------|
| Arquivo não encontrado | Arquivo de entrada ausente | Verificar caminho e nome do arquivo |
| Erros de template | Template corrompido | Verificar `.ai-engine/templates/` |
| Conflitos de nomenclatura | Nomenclatura incorreta | Seguir convenções exatas |
| Verificação de prontidão falha | Pré-requisitos ausentes | Completar fase de planejamento primeiro |

### Checklist de Validação
Antes de iniciar implementação:
- [ ] Documento de visão existe e contém detalhes do produto
- [ ] Documento de roadmap existe com fases e épicos
- [ ] Pelo menos um épico existe com valor de negócio definido
- [ ] Pelo menos uma story existe com critérios de aceitação
- [ ] Arquitetura backend define tecnologias específicas
- [ ] Arquitetura frontend define tecnologias específicas

## 🎯 Principais Funcionalidades
- **Fluxo Estruturado** - Abordagem sistemática da visão ao código
- **Baseado em Templates** - Geração consistente de documentos
- **Personas de IA Especializadas** - Expertise de nível sênior para cada tipo de documento
- **Tarefas Granulares** - Tarefas implementáveis e focadas
- **Diretrizes de Arquitetura** - Padrões técnicos e melhores práticas
- **Testes Abrangentes** - Validação unitária, integração e segurança
- **Documentação Primeiro** - Documentação clara em cada passo
- **Integrações Automatizadas** - Criação automática de cards Jira e commits Git

## 👥 Papéis de IA e Expertise
O AI Dev Engine usa papéis especializados de nível sênior:

### Papéis de Planejamento
- **Senior Product Manager** - Criação de visão e roadmap
- **Senior Product Owner** - Desenvolvimento de épicos e stories

### Papéis de Implementação
- **Senior Backend Engineer** - Arquitetura server-side e APIs
- **Senior Frontend Engineer** - Interface de usuário e desenvolvimento client-side
- **Senior Full-Stack Engineer** - Integração frontend-backend
- **Senior QA Engineer** - Estratégias de teste e garantia de qualidade
- **Senior Security Engineer** - Validação de segurança e compliance

## 🤖 Integrações Automáticas

### Integração Jira
- Criação automática de cards Epic, Story e Task
- Cards linkados hierarquicamente
- Labels de workflow automáticas

### Controle de Versão
- Commits automáticos após criação/modificação de arquivos
- Mensagens de commit convencionais
- Usuário controla quando fazer push

## 📚 Recursos Adicionais
- [Guia do Usuário](docs/user-guide.md) - Uso avançado e personalização
- Templates em `.ai-engine/templates/` - Personalizar estrutura de documentos
- Papéis em `.ai-engine/roles/` - Definições de personas de IA
- Diretrizes de arquitetura em `.ai-engine/architecture/` - Padrões técnicos

## ⚙️ Configuração Inicial

### Configuração Jira (Opcional)
Para usar a integração automática com Jira:

1. **Configure suas credenciais** em `.ai-engine/automations/jira.md`
2. **Substitua os placeholders**:
   - `{JIRA_PROJECT_KEY}` → sua chave de projeto
   - `{JIRA_ACCOUNT_ID}` → seu Account ID do Jira
3. **Veja o exemplo** em `.ai-engine/config/jira.example.md`

**Nota**: A integração Jira é opcional. O sistema funciona perfeitamente sem ela.

## 🚀 Como Começar
1. **Preencha `product-idea.md`** com detalhes do seu projeto
2. **Configure integrações** (opcional) - veja seção de Configuração Inicial
3. **Execute os prompts de planejamento** em sequência
4. **Execute `execute readiness-check`** para validar pré-requisitos
5. **Execute prompts de implementação** para cada user story
6. **Implemente tarefas** usando `execute task-implementation`

Comece com um projeto simples para se familiarizar com o fluxo!

---
**Versão:** 1.0 | **AI Dev Engine** - Da Visão ao Código
