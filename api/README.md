<p align="center">
  <img src="../Thumbnail.png" alt="Thumbnail do projeto Help Desk" width="100%" />
</p>

<h1 align="center">Help Desk API</h1>

<p align="center">
  Backend da plataforma de suporte técnico com autenticação JWT, controle por perfil e gerenciamento completo de chamados.
</p>

<p align="center">
  <strong>Node.js</strong> - <strong>TypeScript</strong> - <strong>Express</strong> - <strong>Prisma</strong> - <strong>PostgreSQL</strong> - <strong>Zod</strong> - <strong>JWT</strong> - <strong>Multer</strong>
</p>

## Sobre

Esta API centraliza toda a regra de negócio do Help Desk. Ela autentica usuários, organiza técnicos por disponibilidade de horário, controla serviços, clientes e chamados, além de proteger o acesso com permissões por perfil.

O fluxo principal do projeto funciona assim:

- clientes criam conta e abrem chamados;
- a API escolhe automaticamente um técnico disponível no horário atual;
- administradores acompanham a operação inteira;
- técnicos assumem seus atendimentos, atualizam status e adicionam serviços extras;
- clientes e técnicos podem atualizar perfil e avatar.

## Funcionalidades

- Cadastro de clientes com senha criptografada usando `bcrypt`.
- Login com geração de token JWT com expiração de `1d`.
- Controle de acesso por perfil: `admin`, `technician` e `customer`.
- Cadastro e edição de técnicos com horários disponíveis.
- Cadastro, listagem e atualização de serviços.
- Criação de chamados com atribuição automática do técnico menos recentemente acionado.
- Listagem de chamados filtrada conforme o perfil autenticado.
- Atualização de status por administradores e técnicos.
- Upload de avatar com `multer`.
- Seed inicial com horários, administrador, serviços e técnicos.

## Estrutura

```text
api
|- prisma
|  |- migrations
|  |- schema.prisma
|  `- seed.ts
|- src
|  |- configs
|  |- controllers
|  |- database
|  |- middlewares
|  |- providers
|  |- routes
|  |- tests
|  |- types
|  |- utils
|  |- app.ts
|  |- env.ts
|  `- server.ts
`- docker-compose.yml
```

## Rotas principais

- `POST /users` cria um novo cliente.
- `POST /sessions` autentica um usuário.
- `GET /tickets` lista chamados conforme o perfil autenticado.
- `POST /tickets` abre um novo chamado para cliente.
- `PATCH /tickets/:id/status` altera o status do chamado.
- `GET /services` lista serviços disponíveis.
- `POST /services/additional/:ticketId` adiciona serviço extra a um chamado.
- `GET /technicians` lista técnicos cadastrados.
- `GET /customers` lista clientes para administração.
- `POST /uploads/:id` envia avatar para técnico ou cliente.

## Como executar

1. Entre na pasta `api`.
2. Instale as dependências com `npm install`.
3. Crie o arquivo `.env` com base no `.env-example`.
4. Suba o banco com `docker compose up -d`.
5. Rode as migrations e o seed do Prisma.
6. Inicie o servidor em modo de desenvolvimento.

```bash
npx prisma migrate dev
npx prisma db seed
npm run dev
```

Por padrão, a API sobe em `http://localhost:3333`.

## Variáveis de ambiente

Use este modelo no seu `.env`:

```env
DATABASE_URL="postgres://postgres:postgres@localhost:5432/helpdesk?schema=public"
JWT_SECRET="seu_secret"
PORT=3333
ADMIN_PASSWORD="sua_senha"
```

## Scripts

- `npm run dev` inicia a API com `tsx watch`.
- `npm run test:dev` executa os testes do Jest em modo watch.
- `npx prisma migrate dev` aplica as migrations no ambiente local.
- `npx prisma db seed` popula o banco com dados iniciais.

## Seed inicial

Depois do seed, o projeto já fica com:

- 1 administrador: `user.adm@email.com`
- 3 técnicos pré-cadastrados
- grade de horários de `07:00` até `23:00`
- serviços iniciais para abertura e composição de chamados

A senha do administrador vem da variável `ADMIN_PASSWORD`.

## Observações

- Os uploads são processados a partir da pasta `tmp`.
- A rota pública de arquivos é servida em `/uploads`, mas exige autenticação.
- O banco utilizado no projeto é PostgreSQL, configurado com Prisma ORM.

## AUTOR 

- Arthur 