# Roadmap

## Objetivo

Este documento descreve o planejamento de desenvolvimento do Nexora ERP.

O projeto será desenvolvido de forma incremental, dividido em versões (milestones) e sprints.

Cada versão deverá entregar funcionalidades completas, testadas e documentadas.

---

# Versão 0.1.0 - Fundação

## Objetivo

Preparar toda a infraestrutura do projeto.

### Backend

* [ ] Inicializar projeto Node.js
* [ ] Configurar TypeScript
* [ ] Configurar Express
* [ ] Configurar Sequelize
* [ ] Configurar PostgreSQL
* [ ] Configurar Docker
* [ ] Configurar variáveis de ambiente
* [ ] Configurar ESLint
* [ ] Configurar Prettier
* [ ] Configurar Husky
* [ ] Configurar lint-staged

### Frontend

* [ ] Inicializar projeto Next.js
* [ ] Configurar Tailwind CSS
* [ ] Configurar React Query
* [ ] Configurar React Hook Form
* [ ] Configurar ESLint
* [ ] Configurar Prettier

### Documentação

* [x] README
* [x] Arquitetura
* [x] Requisitos
* [x] Modelagem do banco
* [ ] API
* [ ] Padrões do projeto

---

# Versão 0.2.0 - Autenticação

## Objetivo

Construir toda a base de autenticação do sistema.

### Funcionalidades

* [ ] Cadastro
* [ ] Login
* [ ] Logout
* [ ] Refresh Token
* [ ] Recuperação de senha
* [ ] Redefinição de senha
* [ ] Alteração de senha
* [ ] Middleware de autenticação

---

# Versão 0.3.0 - Empresas

## Objetivo

Implementar o conceito de multiempresa.

### Funcionalidades

* [ ] CRUD de empresas
* [ ] Empresa ativa
* [ ] Convite de usuários
* [ ] Associação usuário × empresa
* [ ] Configurações da empresa

---

# Versão 0.4.0 - Usuários e Permissões

## Objetivo

Controlar acesso ao sistema.

### Funcionalidades

* [ ] CRUD de usuários
* [ ] Perfis
* [ ] Permissões
* [ ] RBAC
* [ ] Controle de acesso

---

# Versão 0.5.0 - Clientes

## Objetivo

Gerenciar clientes.

### Funcionalidades

* [ ] Cadastro
* [ ] Edição
* [ ] Exclusão
* [ ] Endereços
* [ ] Contatos
* [ ] Pesquisa
* [ ] Paginação
* [ ] Filtros

---

# Versão 0.6.0 - Produtos

## Objetivo

Gerenciar produtos.

### Funcionalidades

* [ ] Cadastro
* [ ] Categorias
* [ ] Upload de imagens
* [ ] SKU
* [ ] Código de barras
* [ ] Pesquisa
* [ ] Paginação

---

# Versão 0.7.0 - Estoque

## Objetivo

Controlar movimentações de estoque.

### Funcionalidades

* [ ] Entrada
* [ ] Saída
* [ ] Ajustes
* [ ] Histórico
* [ ] Estoque mínimo

---

# Versão 0.8.0 - Pedidos

## Objetivo

Gerenciar vendas.

### Funcionalidades

* [ ] Cadastro de pedidos
* [ ] Itens
* [ ] Descontos
* [ ] Status
* [ ] Cancelamento

---

# Versão 0.9.0 - Financeiro

## Objetivo

Gerenciar receitas e despesas.

### Funcionalidades

* [ ] Receitas
* [ ] Despesas
* [ ] Fluxo de caixa
* [ ] Categorias
* [ ] Filtros

---

# Versão 1.0.0 - Dashboard e Relatórios

## Objetivo

Finalizar a primeira versão pública.

### Dashboard

* [ ] Receita
* [ ] Despesas
* [ ] Produtos
* [ ] Clientes
* [ ] Pedidos

### Relatórios

* [ ] CSV
* [ ] PDF
* [ ] Filtros
* [ ] Exportação

### Configurações

* [ ] Preferências do usuário
* [ ] Configurações da empresa

---

# Versão 1.1.0

Melhorias de arquitetura.

* [ ] Testes unitários
* [ ] Testes de integração
* [ ] Cobertura de testes
* [ ] Logs
* [ ] Swagger
* [ ] Health Check

---

# Versão 1.2.0

Melhorias de infraestrutura.

* [ ] Redis
* [ ] Cache
* [ ] Rate Limiting
* [ ] Filas
* [ ] Processamento assíncrono

---

# Versão 1.3.0

Melhorias de experiência do usuário.

* [ ] Tema escuro
* [ ] Internacionalização
* [ ] Upload múltiplo
* [ ] Notificações

---

# Futuras Versões

Possíveis funcionalidades:

* Chat interno
* WebSockets
* Aplicativo mobile
* Integrações externas
* Emissão de notas fiscais
* Gateway de pagamento
* IA para análise de dados
* PWA

---

# Critério de Conclusão

Uma funcionalidade somente será considerada concluída quando atender aos seguintes critérios:

* Código implementado.
* Testes realizados.
* Documentação atualizada.
* Commit realizado seguindo o padrão do projeto.
* Revisão do código concluída.

---

# Histórico de Versões

| Versão | Status                |
| ------ | --------------------- |
| 0.1.0  | 🚧 Em desenvolvimento |
| 0.2.0  | ⏳ Planejada           |
| 0.3.0  | ⏳ Planejada           |
| 0.4.0  | ⏳ Planejada           |
| 0.5.0  | ⏳ Planejada           |
| 0.6.0  | ⏳ Planejada           |
| 0.7.0  | ⏳ Planejada           |
| 0.8.0  | ⏳ Planejada           |
| 0.9.0  | ⏳ Planejada           |
| 1.0.0  | ⏳ Planejada           |
