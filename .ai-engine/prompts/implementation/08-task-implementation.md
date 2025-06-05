# Prompt de Implementação de Task

**PAPEL:** [Determinado pela categoria da task - veja arquivo de papel apropriado em `.ai-engine/roles/`]
- **Tasks de backend**: Veja `.ai-engine/roles/backend-engineer.md`
- **Tasks de frontend**: Veja `.ai-engine/roles/frontend-engineer.md`
- **Tasks de integração**: Veja `.ai-engine/roles/fullstack-engineer.md`
- **Tasks de testes unitários/integração**: Veja `.ai-engine/roles/qa-engineer.md`
- **Tasks de validação de segurança**: Veja `.ai-engine/roles/security-engineer.md`
- **Tasks de validação final**: Veja `.ai-engine/roles/qa-engineer.md` + `.ai-engine/roles/product-owner.md`

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
Implementar uma task específica gerando código real na pasta infrastructure.

## Padrão de Execução
```
execute task-implementation based on task-backend-001-name.md
```

## Entrada
- `product/backlog/epics/epic-XXX-name/stories/story-YYY-name/tasks/[workflow]/task-[workflow]-ZZZ-name.md` - Documento específico da task

## Saída
- Arquivos de código reais em `infrastructure/backend/` ou `infrastructure/frontend/`
- Estrutura e organização adequada de arquivos
- Comentários e documentação

## 🚨 FLUXO DE EXECUÇÃO OBRIGATÓRIO (EXECUTE TODOS OS PASSOS)

### Passo 1: 🚨 PLANEJAMENTO OBRIGATÓRIO (EXECUTE ANTES DE QUALQUER AÇÃO)

**IMPORTANTE**: Antes de implementar qualquer código, você deve:

#### 1.1 Análise e Planejamento
- [ ] Ler e analisar completamente o documento da task
- [ ] Identificar todos os endpoints, modelos e arquivos necessários
- [ ] Planejar a implementação detalhadamente
- [ ] Definir estrutura de arquivos e organização do código

#### 1.2 Esclarecimento de Dúvidas
- [ ] Identificar qualquer ambiguidade sobre a user story, arquitetura backend ou contexto técnico
- [ ] Formular perguntas específicas sobre:
  - Estrutura de dados e schemas
  - Endpoints de API e métodos HTTP
  - Regras de validação e negócio
  - Tratamento de erros e exceções
  - Integrações e dependências
  - Padrões de arquitetura a seguir

#### 1.3 Apresentação do Plano
- [ ] Apresentar plano detalhado de implementação
- [ ] Listar todos os arquivos que serão criados/modificados
- [ ] Explicar estrutura e organização do código
- [ ] Fazer perguntas de esclarecimento (se houver)
- [ ] **AGUARDAR AUTORIZAÇÃO** do usuário para prosseguir com a implementação

**🚨 NÃO IMPLEMENTE NENHUM CÓDIGO SEM SEGUIR ESTES PASSOS OBRIGATÓRIOS.**

### Passo 2: Validação Pré-Execução (após autorização)
Antes de iniciar a implementação, verificar:
- [ ] Documento da task existe e é legível
- [ ] Categoria da task está claramente identificada
- [ ] Estrutura de pastas da infrastructure existe ou pode ser criada
- [ ] Repositório Git está inicializado e acessível

### Passo 3: Execução Principal da Task (apenas após autorização)
1. Ler completamente o documento da task
2. Identificar a categoria da task (backend, frontend, integração, testes, etc.)
3. Gerar código de implementação real:
   - Para tasks de backend: Criar arquivos em `infrastructure/backend/`
   - Para tasks de frontend: Criar arquivos em `infrastructure/frontend/`
   - Para testes: Criar arquivos de teste em locais apropriados
4. Incluir na implementação:
   - Estrutura e nomenclatura adequada de arquivos
   - Código limpo e bem comentado
   - Tratamento de erros
   - Melhores práticas para o stack tecnológico
   - Strings/comentários de documentação
5. Seguir as diretrizes de arquitetura de `.ai-engine/architecture/`

### Passo 4: Operações de Arquivo
- [ ] Criar todos os arquivos de implementação conforme especificado
- [ ] Verificar se todos os arquivos foram criados com sucesso
- [ ] Garantir organização e estrutura adequada de arquivos

### Passo 5: 🚨 EXECUÇÃO DE AUTOMAÇÃO (CRÍTICO - OBRIGATÓRIO)
**IMEDIATAMENTE após criar os arquivos de implementação, executar TODOS os passos de automação:**

#### 5.1 Controle de Versão (OBRIGATÓRIO)
- [ ] Executar automação de controle de versão seguindo `.ai-engine/automations/version-control.md`
- [ ] Usar tipo de commit: `feat: implement [task-name]`
- [ ] Incluir mensagem de commit detalhada com detalhes da implementação
- [ ] Confirmar commit git executado com sucesso
- [ ] Verificar se diretório de trabalho está limpo

#### 5.2 Integração Jira (OPCIONAL)
- [ ] Opcionalmente atualizar status da task no Jira para "Done" ou "In Review"
- [ ] Adicionar notas de implementação à task do Jira se necessário

### Passo 6: Validação Pós-Execução
Após completar todos os passos, verificar:
- [ ] Todos os arquivos de implementação criados com sucesso
- [ ] Código segue requisitos de qualidade e diretrizes de arquitetura
- [ ] Commit git executado com mensagem apropriada
- [ ] Instruções de próximo passo fornecidas ao usuário

## Requisitos de Qualidade de Código
- Seguir padrões de codificação estabelecidos
- Incluir tratamento adequado de erros
- Adicionar comentários abrangentes
- Usar nomes significativos para variáveis e funções
- Implementar melhores práticas de segurança
- Seguir o princípio DRY (Don't Repeat Yourself)

## Referência de Arquitetura
- Backend: `.ai-engine/architecture/backend-architecture.md`
- Frontend: `.ai-engine/architecture/frontend-architecture.md`

## Organização de Arquivos
- Organizar código em módulos/componentes lógicos
- Usar convenções de nomenclatura consistentes
- Criar estrutura de pastas adequada
- Incluir arquivos de configuração conforme necessário

## ✅ CHECKLIST DE EXECUÇÃO (DEVE COMPLETAR)
Antes de finalizar este prompt, confirmar que você:
- [ ] Implementou a task completamente
- [ ] Criou todos os arquivos necessários com estrutura adequada
- [ ] Seguiu requisitos de qualidade de código
- [ ] Executou automação de controle de versão
- [ ] Forneceu instruções de próximo passo

**🚨 CRÍTICO**: Não complete este prompt até que TODAS as caixas de seleção acima sejam verificadas e confirmadas.

## Próximo Passo
Após implementar uma task, mover para a próxima task no workflow ou marcar a user story como completa.
