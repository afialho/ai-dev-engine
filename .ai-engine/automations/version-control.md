# Regras de Automação de Controle de Versão

## Quando Executar
Executar automação de controle de versão após:
- **Criação de Arquivo**: Quando ferramenta `save-file` é usada
- **Modificação de Arquivo**: Quando ferramenta `str-replace-editor` é usada
- **Remoção de Arquivo**: Quando ferramenta `remove-files` é usada
- **Instalação de Pacotes**: Quando comandos de package manager são executados

## Sequência de Automação
1. **Stage Changes**: Adicionar todos os arquivos modificados
2. **Commit Changes**: Criar commit com formato conventional commit
3. **SEM Push**: Usuário controla quando fazer push para repositório remoto

## Formato Conventional Commit
Usar este formato para mensagens de commit:
```
[type]: [description]

[optional body]

Co-authored-by: Augment Code <https://www.augmentcode.com>
```

## Tipos de Commit por Prompt
- **epic-generator**: `docs: generate epic [epic-name]`
- **story-generator**: `docs: generate stories for [epic-name]`
- **backend-tasks-generator**: `feat: generate backend tasks for [story-name]`
- **frontend-tasks-generator**: `feat: generate frontend tasks for [story-name]`
- **front-back-integration-tasks-generator**: `feat: generate integration tasks for [story-name]`
- **unit-tests-tasks-generator**: `test: generate unit test tasks for [story-name]`
- **integration-tests-tasks-generator**: `test: generate integration test tasks for [story-name]`
- **security-validation-tasks-generator**: `feat: generate security validation tasks for [story-name]`
- **final-validation-tasks-generator**: `feat: generate final validation tasks for [story-name]`
- **task-implementation**: `feat: implement [task-name]`

## Convenções de Nomenclatura
- **Epics**: `epic-001-name`, `epic-002-name` (numeração globalmente única)
- **Stories**: `story-001-name`, `story-002-name` (numeração globalmente única)
- **Tasks**: `task-[workflow]-001-name` (numeração globalmente única em todos os workflows)

## Referência de Tipos de Commit
- **feat**: Implementação de nova funcionalidade ou geração de task
- **fix**: Correções de bugs
- **docs**: Mudanças de documentação (epics, stories, docs de planejamento)
- **test**: Adição ou atualização de testes
- **refactor**: Refatoração de código sem mudanças de funcionalidade
- **style**: Mudanças de estilo de código (formatação, etc.)
- **chore**: Tarefas de manutenção, mudanças de build

## Exemplos de Mensagens de Commit
```bash
# Para geração de epic
docs: generate epic user authentication system

# Para tasks de backend
feat: generate backend tasks for user login story

# Para implementação de task
feat: implement user registration API endpoint

- Add POST /api/auth/register endpoint
- Add input validation for email and password
- Add password hashing with bcrypt
- Add user creation in database

Co-authored-by: Augment Code <https://www.augmentcode.com>
```

## Requisitos de Autorização
- **Commits**: Executar automaticamente após conclusão bem-sucedida do prompt
- **Push**: Requer autorização explícita do usuário - NUNCA fazer auto-push
- **Operações de Branch**: Usuário controla estratégia de branching

## Tratamento de Erros
- Se commit falhar, registrar erro mas continuar com execução do prompt
- Sempre completar o objetivo principal do prompt independentemente de falhas de automação
- Notificar usuário sobre quaisquer problemas de controle de versão
