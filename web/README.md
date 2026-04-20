<p align="center">
  <img src="../Thumbnail.png" alt="Thumbnail do projeto Help Desk" width="100%" />
</p>

<h1 align="center">Help Desk Web</h1>

<p align="center">
  Frontend da plataforma de atendimento técnico com navegação por perfil, autenticação persistida e interface para abertura e acompanhamento de chamados.
</p>

<p align="center">
  <strong>React 19</strong> - <strong>TypeScript</strong> - <strong>Vite</strong> - <strong>Tailwind CSS 4</strong> - <strong>React Router 7</strong> - <strong>Axios</strong> - <strong>React Hook Form</strong> - <strong>Zod</strong>
</p>

## Sobre

Esta aplicação web consome a API do projeto Help Desk e organiza a experiência conforme o perfil logado. Assim que o usuário entra no sistema, o frontend identifica sua função e redireciona para as rotas adequadas de administração, atendimento técnico ou abertura de chamados.

## O que a interface entrega

- Login e cadastro com persistência da sessão em `localStorage`.
- Separação automática das rotas para `admin`, `technician` e `customer`.
- Listagem de chamados com tela de detalhes.
- Abertura de novo chamado pelo cliente.
- Gestão de técnicos, clientes e serviços pelo administrador.
- Formulários com validação usando `react-hook-form` + `zod`.
- Componentes reutilizáveis para layout, botões, inputs, navegação e tabelas.

## Estrutura

```text
web
|- public
|- src
|  |- assets
|  |- components
|  |- contexts
|  |- dtos
|  |- hooks
|  |- pages
|  |- routes
|  |- services
|  |- types
|  |- utils
|  |- App.tsx
|  |- index.css
|  `- main.tsx
|- vite.config.ts
`- eslint.config.js
```

## Perfis da aplicação

- `admin`: visualiza chamados, consulta detalhes e gerencia técnicos, clientes e serviços.
- `technician`: acompanha os chamados atribuídos e acessa os detalhes do atendimento.
- `customer`: abre chamados, acompanha o andamento e consulta os detalhes da solicitação.

## Como executar

1. Entre na pasta `web`.
2. Instale as dependências com `npm install`.
3. Certifique-se de que a API esteja rodando em `http://localhost:3333`.
4. Inicie o servidor de desenvolvimento do Vite.

```bash
npm install
npm run dev
```

Depois disso, a aplicação ficará disponível no endereço exibido pelo Vite, normalmente `http://localhost:5173`.

## Integração com a API

O frontend usa `axios` com base URL fixa em `http://localhost:3333`, definida em `src/services/api.ts`.

Se você mudar a porta ou hospedar a API em outro endereço, atualize esse arquivo antes de rodar o projeto.

## Scripts

- `npm run dev` inicia o ambiente local com Vite.
- `npm run build` gera a versão de produção.
- `npm run preview` sobe uma prévia local do build.
- `npm run lint` executa a análise estática com ESLint.

## Fluxo de autenticação

- A sessão fica armazenada com a chave `@helpdesk`.
- O token JWT é reaproveitado nas requisições autenticadas.
- Quando a API responde `401`, o contexto remove a sessão local e redireciona para a tela inicial.

## Observações

- Este módulo depende da API para autenticação, listagem e manipulação dos dados.
- Os assets visuais e páginas já estão organizados por contexto de uso, o que facilita evolução e manutenção.
- O projeto utiliza Tailwind CSS 4 com Vite Plugin para estilização.

## AUTOR 

- Arthur 