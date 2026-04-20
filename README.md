<p align="center">
  <img src="./Thumbnail.png" alt="Thumbnail do projeto Help Desk" width="100%" />
</p>

<h1 align="center">Help Desk</h1>

<p align="center">
  Plataforma full stack para abertura, distribuição e acompanhamento de chamados de suporte técnico.
</p>

<p align="center">
  <strong>API</strong> em Node.js, TypeScript, Express, Prisma e PostgreSQL<br />
  <strong>Web</strong> em React, TypeScript, Vite e Tailwind CSS
</p>

## Visão geral

O projeto foi separado em dois módulos principais:

- `api/`: backend com autenticação JWT, regras de negócio, gerenciamento de usuários, serviços, técnicos e chamados.
- `web/`: frontend com rotas por perfil, autenticação persistida e interface para clientes, técnicos e administradores.

## Estrutura

```text
Help-Desk
|- api
|- web
|- Thumbnail.png
`- README.md
```

## Documentação por módulo

- [API README](./api/README.md)
- [Web README](./web/README.md)

## Como rodar o projeto

1. Suba a API:

```bash
cd api
npm install
docker compose up -d
npx prisma migrate dev
npx prisma db seed
npm run dev
```

2. Em outro terminal, suba o frontend:

```bash
cd web
npm install
npm run dev
```

## Tecnologias

- Node.js
- TypeScript
- Express
- Prisma ORM
- PostgreSQL
- React
- Vite
- Tailwind CSS

## Observação

As instruções detalhadas de configuração, rotas e scripts estão nos READMEs específicos da [API](./api/README.md) e do [Web](./web/README.md).
