# Modelagem do Banco de Dados

## Objetivo

Este documento descreve o modelo conceitual do banco de dados do Nexora ERP.

O objetivo é identificar as entidades do domínio, seus relacionamentos e responsabilidades antes da implementação física utilizando PostgreSQL e Sequelize.

A modelagem poderá evoluir durante o desenvolvimento do projeto.

---

# Visão Geral

O Nexora ERP será um sistema multiempresa (multi-tenant).

Um usuário poderá participar de uma ou mais empresas, e cada empresa possuirá seus próprios clientes, produtos, pedidos e movimentações financeiras.

---

# Entidades do Domínio

## Usuários (Users)

Representam as pessoas que possuem acesso ao sistema.

Responsabilidades:

* Autenticação
* Perfil do usuário
* Preferências pessoais
* Participação em empresas

Relacionamentos:

* Um usuário pode participar de várias empresas.
* Um usuário pode possuir vários Refresh Tokens.
* Um usuário pode possuir diferentes perfis em empresas diferentes.

---

## Empresas (Companies)

Representam as empresas cadastradas no sistema.

Responsabilidades:

* Dados da empresa
* Configurações
* Proprietário
* Usuários vinculados

Relacionamentos:

* Uma empresa possui vários usuários.
* Uma empresa possui vários clientes.
* Uma empresa possui vários produtos.
* Uma empresa possui vários pedidos.
* Uma empresa possui várias transações financeiras.

---

## Company Members

Entidade responsável por relacionar usuários e empresas.

Ela permitirá que:

* Um usuário participe de várias empresas.
* Uma empresa possua vários usuários.
* Cada usuário tenha uma função específica dentro da empresa.

Relacionamentos:

Users

⇄

Company Members

⇄

Companies

---

## Roles

Representam perfis de acesso.

Exemplos:

* Administrator
* Manager
* Sales
* Finance
* Inventory

---

## Permissions

Representam permissões individuais do sistema.

Exemplos:

* Create Customer
* Edit Customer
* Delete Customer
* View Reports

Relacionamentos:

Role

↓

Role Permissions

↓

Permission

---

## Customers

Representam os clientes de uma empresa.

Relacionamentos:

* Pertencem a uma empresa.
* Possuem endereços.
* Possuem contatos.
* Possuem pedidos.

---

## Customer Addresses

Endereços dos clientes.

Um cliente poderá possuir vários endereços.

---

## Products

Produtos vendidos pela empresa.

Relacionamentos:

* Pertencem a uma empresa.
* Pertencem a uma categoria.
* Possuem movimentações de estoque.
* Podem aparecer em vários pedidos.

---

## Categories

Categorias utilizadas para organizar produtos.

Uma categoria poderá conter vários produtos.

---

## Inventory

Representa o estoque atual dos produtos.

Cada produto possuirá um controle de estoque.

---

## Inventory Movements

Responsável por registrar toda movimentação realizada no estoque.

Exemplos:

* Entrada
* Saída
* Ajuste

Nenhuma alteração de estoque deverá ocorrer sem gerar uma movimentação.

---

## Orders

Representam pedidos realizados pelos clientes.

Relacionamentos:

* Pertencem a uma empresa.
* Possuem um cliente.
* Possuem vários itens.

---

## Order Items

Itens pertencentes aos pedidos.

Relacionamentos:

Pedido

↓

Itens

↓

Produto

---

## Financial Transactions

Representam receitas e despesas.

Exemplos:

* Venda
* Compra
* Pagamento
* Recebimento
* Despesas administrativas

---

## Reports

Os relatórios serão gerados a partir das informações armazenadas nas demais entidades.

Nenhuma informação será armazenada exclusivamente para relatórios.

---

# Relacionamento Geral

```text
Users
│
├── Refresh Tokens
│
└── Company Members
      │
      ├── Companies
      │      │
      │      ├── Customers
      │      │      └── Customer Addresses
      │      │
      │      ├── Products
      │      │      ├── Categories
      │      │      └── Inventory
      │      │             └── Inventory Movements
      │      │
      │      ├── Orders
      │      │      └── Order Items
      │      │
      │      └── Financial Transactions
      │
      └── Roles
             └── Permissions
```

---

# Convenções

* Todas as tabelas utilizarão UUID como chave primária.
* Todas as tabelas possuirão `created_at` e `updated_at`.
* Sempre que necessário será utilizado `deleted_at` para Soft Delete.
* Chaves estrangeiras seguirão o padrão `<entity>_id`.
* Nomes de tabelas serão escritos no plural.
* Nomes de colunas serão escritos em `snake_case`.

---

# Próximos Passos

Após a validação deste documento serão definidos:

* Campos de cada entidade.
* Tipos de dados.
* Índices.
* Chaves estrangeiras.
* Restrições.
* Estratégias de exclusão.
* Migrations do Sequelize.
