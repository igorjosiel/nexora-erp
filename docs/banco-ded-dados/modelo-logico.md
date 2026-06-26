# Modelo Lógico

## Objetivo

Este documento descreve o modelo lógico do banco de dados do Nexora ERP.

Seu objetivo é detalhar as entidades do sistema, seus atributos, relacionamentos e regras de integridade antes da implementação física no PostgreSQL.

---

# Convenções

* Todas as entidades utilizarão UUID como chave primária.
* Todas as tabelas possuirão os campos:

  * id
  * created_at
  * updated_at
* Quando necessário será utilizado:

  * deleted_at (Soft Delete)

---

# Users

## Atributos

| Campo         | Tipo      |
| ------------- | --------- |
| id            | UUID      |
| name          | String    |
| email         | String    |
| password      | String    |
| avatar        | String    |
| status        | Enum      |
| last_login_at | Timestamp |
| created_at    | Timestamp |
| updated_at    | Timestamp |

## Relacionamentos

* User 1:N Refresh Tokens
* User N:N Companies
* User N:1 Role (por empresa)

---

# Refresh Tokens

## Atributos

| Campo      | Tipo      |
| ---------- | --------- |
| id         | UUID      |
| user_id    | UUID      |
| token      | String    |
| expires_at | Timestamp |
| revoked_at | Timestamp |

## Relacionamentos

* Refresh Token N:1 User

---

# Companies

## Atributos

| Campo      | Tipo      |
| ---------- | --------- |
| id         | UUID      |
| name       | String    |
| legal_name | String    |
| document   | String    |
| email      | String    |
| phone      | String    |
| created_at | Timestamp |
| updated_at | Timestamp |

## Relacionamentos

* Company N:N Users
* Company 1:N Customers
* Company 1:N Products
* Company 1:N Orders
* Company 1:N Financial Transactions

---

# Company Members

## Atributos

| Campo      | Tipo      |
| ---------- | --------- |
| id         | UUID      |
| company_id | UUID      |
| user_id    | UUID      |
| role_id    | UUID      |
| invited_at | Timestamp |
| joined_at  | Timestamp |

## Relacionamentos

* N:1 User
* N:1 Company
* N:1 Role

---

# Roles

## Atributos

| Campo       | Tipo   |
| ----------- | ------ |
| id          | UUID   |
| company_id  | UUID   |
| name        | String |
| description | String |

## Relacionamentos

* Role N:N Permissions
* Role 1:N Company Members

---

# Permissions

## Atributos

| Campo       | Tipo   |
| ----------- | ------ |
| id          | UUID   |
| name        | String |
| description | String |

## Relacionamentos

* Permission N:N Roles

---

# Customers

## Atributos

| Campo      | Tipo   |
| ---------- | ------ |
| id         | UUID   |
| company_id | UUID   |
| name       | String |
| document   | String |
| email      | String |
| phone      | String |
| notes      | Text   |

## Relacionamentos

* Customer N:1 Company
* Customer 1:N Addresses
* Customer 1:N Orders

---

# Customer Addresses

## Atributos

| Campo       | Tipo   |
| ----------- | ------ |
| id          | UUID   |
| customer_id | UUID   |
| zip_code    | String |
| street      | String |
| number      | String |
| district    | String |
| city        | String |
| state       | String |

## Relacionamentos

* Address N:1 Customer

---

# Categories

## Atributos

| Campo       | Tipo   |
| ----------- | ------ |
| id          | UUID   |
| company_id  | UUID   |
| name        | String |
| description | String |

## Relacionamentos

* Category 1:N Products

---

# Products

## Atributos

| Campo         | Tipo    |
| ------------- | ------- |
| id            | UUID    |
| company_id    | UUID    |
| category_id   | UUID    |
| name          | String  |
| sku           | String  |
| barcode       | String  |
| cost_price    | Decimal |
| sale_price    | Decimal |
| minimum_stock | Decimal |

## Relacionamentos

* Product N:1 Company
* Product N:1 Category
* Product 1:1 Inventory
* Product 1:N Inventory Movements
* Product N:N Orders

---

# Inventory

## Atributos

| Campo      | Tipo    |
| ---------- | ------- |
| id         | UUID    |
| product_id | UUID    |
| quantity   | Decimal |

## Relacionamentos

* Inventory 1:1 Product
* Inventory 1:N Inventory Movements

---

# Inventory Movements

## Atributos

| Campo        | Tipo    |
| ------------ | ------- |
| id           | UUID    |
| inventory_id | UUID    |
| type         | Enum    |
| quantity     | Decimal |
| reason       | String  |

## Relacionamentos

* Movement N:1 Inventory

---

# Orders

## Atributos

| Campo       | Tipo    |
| ----------- | ------- |
| id          | UUID    |
| company_id  | UUID    |
| customer_id | UUID    |
| status      | Enum    |
| total       | Decimal |
| discount    | Decimal |

## Relacionamentos

* Order N:1 Customer
* Order 1:N Order Items

---

# Order Items

## Atributos

| Campo      | Tipo    |
| ---------- | ------- |
| id         | UUID    |
| order_id   | UUID    |
| product_id | UUID    |
| quantity   | Decimal |
| unit_price | Decimal |
| total      | Decimal |

## Relacionamentos

* Item N:1 Order
* Item N:1 Product

---

# Financial Transactions

## Atributos

| Campo      | Tipo    |
| ---------- | ------- |
| id         | UUID    |
| company_id | UUID    |
| type       | Enum    |
| category   | String  |
| amount     | Decimal |
| due_date   | Date    |
| paid_at    | Date    |

## Relacionamentos

* Transaction N:1 Company

---

# Cardinalidades

| Origem    | Relacionamento | Destino               |
| --------- | -------------- | --------------------- |
| User      | 1:N            | Refresh Tokens        |
| User      | N:N            | Company               |
| Company   | 1:N            | Customer              |
| Company   | 1:N            | Product               |
| Company   | 1:N            | Category              |
| Company   | 1:N            | Order                 |
| Company   | 1:N            | Financial Transaction |
| Customer  | 1:N            | Address               |
| Customer  | 1:N            | Order                 |
| Category  | 1:N            | Product               |
| Product   | 1:1            | Inventory             |
| Inventory | 1:N            | Inventory Movement    |
| Order     | 1:N            | Order Item            |
| Product   | 1:N            | Order Item            |
| Role      | N:N            | Permission            |

---

# Próxima Etapa

Após a aprovação deste modelo lógico, será criado o modelo físico do banco de dados contendo:

* Tipos do PostgreSQL
* Índices
* Constraints
* Chaves estrangeiras
* Estratégias de exclusão
* Migrations do Sequelize
