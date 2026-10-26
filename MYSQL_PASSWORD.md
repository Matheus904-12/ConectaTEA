# Configuração segura do banco de dados

Este documento não deve conter senhas, tokens ou credenciais reais.

Configure as variáveis abaixo no ambiente de hospedagem ou em um arquivo `.env` local que não seja versionado:

- `DB_HOST`
- `DB_PORT`
- `DB_NAME`
- `DB_USER`
- `DB_PASSWORD`

## Orientações

1. Use credenciais diferentes para desenvolvimento e produção.
2. Conceda à aplicação somente as permissões necessárias.
3. Não compartilhe senhas em Markdown, issues, commits ou prompts de IA.
4. Se uma credencial real já foi publicada, revogue-a ou altere-a no provedor e atualize o ambiente de execução.
5. Remover uma credencial do arquivo atual não remove cópias do histórico Git.

Consulte o README e os arquivos de exemplo do projeto para configurar o ambiente sem registrar segredos.