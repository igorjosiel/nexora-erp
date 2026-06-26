# Modelo Físico

## Objetivo

Este documento descreve a implementação física do banco de dados do Nexora ERP.

São definidos os tipos das colunas, restrições, índices e relacionamentos que serão implementados no PostgreSQL utilizando Sequelize.

---

# Convenções

## Chave Primária

Todas as tabelas utilizarão UUID como chave primária.

```sql
id UUID PRIMARY KEY
```

---

## Auditoria

Todas as tabelas possuirão:

| Campo      | Tipo      |
| ---------- | --------- |
| created_at | TIMESTAMP |
| updated_at | TIMESTAMP |

Quando necessário:

| Campo      | Tipo      |
| ---------- | --------- |
| deleted_at | TIMESTAMP |

---

## Chaves Estrangeiras

Padrão:

```text
<entity>_id
```

Exemplos:

```text
company_id
user_id
customer_id
product_id
role_id
```

---

## Convenção de nomes

Tabela:

```text
snake_case
plural
```

Exemplo:

```text
users
companies
order_items
inventory_movements
financial_transactions
```

Colunas:

```text
snake_case
```

---

# Users

## Campos

| Campo         | PostgreSQL   | Restrições      |
| ------------- | ------------ | --------------- |
| id            | UUID         | PK              |
| name          | VARCHAR(150) | NOT NULL        |
| email         | VARCHAR(255) | NOT NULL UNIQUE |
| password      | VARCHAR(255) | NOT NULL        |
| avatar        | TEXT         | NULL            |
| status        | SMALLINT     | DEFAULT 1       |
| last_login_at | TIMESTAMP    | NULL            |
| created_at    | TIMESTAMP    | NOT NULL        |
| updated_at    | TIMESTAMP    | NOT NULL        |
| deleted_at    | TIMESTAMP    | NULL            |

## Índices

```text
email
status
```

---

# Refresh Tokens

| Campo      | Tipo      | Restrições |
| ---------- | --------- | ---------- |
| id         | UUID      | PK         |
| user_id    | UUID      | FK         |
| token      | TEXT      | UNIQUE     |
| expires_at | TIMESTAMP | NOT NULL   |
| revoked_at | TIMESTAMP | NULL       |
| created_at | TIMESTAMP | NOT NULL   |

## Foreign Keys

```text
user_id

ON DELETE CASCADE

ON UPDATE CASCADE
```

---

# Companies

| Campo      | Tipo         | Restrições |
| ---------- | ------------ | ---------- |
| id         | UUID         | PK         |
| name       | VARCHAR(150) | NOT NULL   |
| legal_name | VARCHAR(255) | NOT NULL   |
| document   | VARCHAR(20)  | UNIQUE     |
| email      | VARCHAR(255) | NULL       |
| phone      | VARCHAR(20)  | NULL       |
| created_at | TIMESTAMP    | NOT NULL   |
| updated_at | TIMESTAMP    | NOT NULL   |
| deleted_at | TIMESTAMP    | NULL       |

Índices:

```text
document
name
```

---

# Company Members

| Campo      | Tipo      |
| ---------- | --------- |
| id         | UUID      |
| company_id | UUID      |
| user_id    | UUID      |
| role_id    | UUID      |
| invited_at | TIMESTAMP |
| joined_at  | TIMESTAMP |

Foreign Keys

```text
company_id

ON DELETE CASCADE

user_id

ON DELETE CASCADE

role_id

ON DELETE RESTRICT
```

Índice composto

```text
(company_id, user_id)
```

UNIQUE

```text
(company_id, user_id)
```

---

# Roles

Campos

```text
id
company_id
name
description
created_at
updated_at
```

UNIQUE

```text
(company_id, name)
```

---

# Permissions

Campos

```text
id
name
description
created_at
updated_at
```

UNIQUE

```text
name
```

---

# Role Permissions

Tabela de relacionamento N:N

Campos

```text
role_id

permission_id
```

PK composta

```text
(role_id, permission_id)
```

---

# Customers

Campos

```text
id

company_id

name

document

email

phone

notes

created_at

updated_at

deleted_at
```

Índices

```text
company_id

name

document
```

---

# Customer Addresses

Campos

```text
id

customer_id

zip_code

street

number

district

city

state

country

created_at

updated_at
```

---

# Categories

Campos

```text
id

company_id

name

description

created_at

updated_at
```

UNIQUE

```text
(company_id, name)
```

---

# Products

Campos

```text
id

company_id

category_id

name

sku

barcode

cost_price NUMERIC(12,2)

sale_price NUMERIC(12,2)

minimum_stock NUMERIC(12,2)

created_at

updated_at

deleted_at
```

Índices

```text
company_id

category_id

sku

barcode
```

---

# Inventory

Campos

```text
id

product_id

quantity NUMERIC(12,2)

created_at

updated_at
```

UNIQUE

```text
product_id
```

---

# Inventory Movements

Campos

```text
id

inventory_id

type

quantity

reason

created_at
```

Índices

```text
inventory_id

type
```

---

# Orders

Campos

```text
id

company_id

customer_id

status

discount

total

created_at

updated_at

deleted_at
```

Índices

```text
company_id

customer_id

status
```

---

# Order Items

Campos

```text
id

order_id

product_id

quantity

unit_price

total

created_at
```

Índices

```text
order_id

product_id
```

---

# Financial Transactions

Campos

```text
id

company_id

type

category

amount NUMERIC(12,2)

due_date

paid_at

created_at

updated_at
```

Índices

```text
company_id

type

due_date
```

---

# Estratégias de Exclusão

| Relacionamento                 | ON DELETE |
| ------------------------------ | --------- |
| User → Refresh Token           | CASCADE   |
| Company → Company Member       | CASCADE   |
| User → Company Member          | CASCADE   |
| Company → Customer             | RESTRICT  |
| Company → Product              | RESTRICT  |
| Customer → Order               | RESTRICT  |
| Product → Order Item           | RESTRICT  |
| Product → Inventory            | CASCADE   |
| Inventory → Inventory Movement | CASCADE   |

---

# Estratégias de Atualização

Todas as Foreign Keys utilizarão:

```text
ON UPDATE CASCADE
```

---

# Próxima Etapa

Com este documento concluído, iniciaremos a implementação das migrations utilizando Sequelize, respeitando todas as definições estabelecidas neste modelo físico.
