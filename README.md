# Controle de Gastos — CI público

Este repositório público existe **somente para CI/testes de infraestrutura** do projeto Controle de Gastos.

Ele **não contém** o código completo do aplicativo, histórico do repositório privado, banco de dados, credenciais, secrets, tokens, chaves OAuth, service accounts, keystore, dados financeiros ou artefatos Android.

## Escopo

- Executar testes públicos/sem autenticação contra o **sandbox Floot**.
- Gerar evidência de carga sem tocar em produção.
- Reduzir o uso de GitHub Actions do repositório privado.

## Acesso protegido ao sandbox

O sandbox Floot pode exigir um preview token temporário. O workflow lê esse valor somente do GitHub Actions Secret chamado `FLOOT_PREVIEW_TOKEN`.

- O token **nunca** deve ser commitado neste repositório.
- O workflow é `workflow_dispatch` apenas; não executa em pull requests públicos.
- O token não é impresso nos logs.
- Quando o preview token expirar, apenas o Secret deve ser atualizado.

## Segurança

O workflow valida o destino antes de iniciar e recusa qualquer host que não termine em `.sandbox.floot.app`.

Nunca adicionar neste repositório:

- `.env` ou arquivos equivalentes;
- credenciais de banco;
- secrets de Google/Facebook/Brevo/RevenueCat/AdMob;
- service accounts;
- keystore ou certificados privados;
- backups, dumps ou dados de usuários;
- código-fonte completo do app privado.

A fonte canônica do aplicativo continua fora deste repositório público.
