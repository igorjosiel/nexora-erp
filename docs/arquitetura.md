
# Arquitetura do Projeto

## Visão Geral

O **Nexora ERP** é uma plataforma SaaS de gestão empresarial desenvolvida com foco em escalabilidade, organização do código e boas práticas de engenharia de software.

Este projeto tem como objetivo simular um ambiente de produção real, servindo como um projeto de portfólio para demonstrar conhecimentos em desenvolvimento Full Stack.

---

# Objetivos da Arquitetura

A arquitetura do projeto foi definida com os seguintes objetivos:

* Facilitar a manutenção do sistema.
* Permitir o crescimento da aplicação sem grandes refatorações.
* Separar responsabilidades entre as camadas da aplicação.
* Favorecer a reutilização de código.
* Tornar o projeto fácil de entender para novos desenvolvedores.
* Aplicar boas práticas de desenvolvimento.

---

# Stack Tecnológica

## Backend

* Node.js
* TypeScript
* Express
* Sequelize
* PostgreSQL
* JWT
* Docker

## Frontend

* Next.js
* React
* TypeScript
* Tailwind CSS
* React Query
* React Hook Form

---

# Arquitetura Geral

O projeto será dividido em duas aplicações independentes.

```text
nexora-erp/

├── backend/
├── frontend/
└── docs/
```

Essa separação permite que backend e frontend evoluam de forma independente.

---

# Arquitetura do Backend

O backend será organizado por módulos (Module-Based Architecture).

Cada módulo será responsável por uma funcionalidade do sistema.

Exemplo:

```text
src/

modules/

    auth/

    users/

    companies/

    customers/

    products/

    inventory/

    orders/

    finance/

shared/

    database/

    config/

    middleware/

    errors/

    utils/
```

Cada módulo possuirá sua própria estrutura interna.

```text
users/

controllers/

services/

repositories/

models/

validators/

dtos/

routes/

tests/
```

Essa organização reduz o acoplamento entre funcionalidades e facilita a evolução do sistema.

---

# Arquitetura do Frontend

O frontend seguirá uma organização baseada em funcionalidades e componentes reutilizáveis.

Estrutura inicial:

```text
src/

app/

components/

features/

hooks/

services/

store/

contexts/

validators/

types/

utils/
```

O objetivo é manter os componentes desacoplados e reutilizáveis.

---

# Comunicação

A comunicação entre frontend e backend será realizada através de uma API REST utilizando JSON.

Fluxo:

```text
Frontend

↓

API REST

↓

Backend

↓

PostgreSQL
```

---

# Banco de Dados

O banco de dados utilizado será o PostgreSQL.

O mapeamento objeto-relacional será realizado com Sequelize.

Todas as alterações de estrutura serão controladas por Migrations.

---

# Autenticação

O sistema utilizará autenticação baseada em JWT.

Fluxo previsto:

* Login
* Access Token
* Refresh Token
* Renovação automática do Access Token
* Logout
* Revogação do Refresh Token

Os detalhes serão documentados posteriormente.

---

# Organização dos Módulos

A primeira versão do sistema contará com os seguintes módulos:

* Authentication
* Companies
* Users
* Roles & Permissions
* Dashboard
* Customers
* Products
* Categories
* Inventory
* Orders
* Finance
* Reports
* Settings

Cada módulo será desenvolvido de forma independente.

---

# Convenções

## Idioma

Todo o código será escrito em inglês.

Incluindo:

* Classes
* Interfaces
* Métodos
* Variáveis
* Tabelas
* Colunas
* Rotas
* Commits

A documentação do projeto será escrita em português.

---

## Padrão de Commits

Será utilizado o padrão Conventional Commits.

Exemplos:

```text
feat(auth): implement login endpoint

fix(users): validate duplicated email

refactor(products): simplify repository

docs: update architecture documentation
```

---

# Princípios de Desenvolvimento

Durante o desenvolvimento serão priorizados os seguintes princípios:

* Clean Code
* SOLID
* Separation of Concerns
* DRY (Don't Repeat Yourself)
* KISS (Keep It Simple)
* Baixo acoplamento
* Alta coesão

---

# Evolução da Arquitetura

Este documento será atualizado conforme novas decisões arquiteturais forem tomadas durante o desenvolvimento do projeto.
