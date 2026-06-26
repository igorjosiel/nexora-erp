# Requisitos do Sistema

## Objetivo

Este documento descreve os requisitos funcionais do Nexora ERP.

Seu objetivo é definir o comportamento esperado do sistema antes da implementação, servindo como referência para a modelagem do banco de dados, desenvolvimento da API e construção da interface.

---

# Escopo da Versão 1.0

A primeira versão do Nexora ERP contará com os seguintes módulos:

* Autenticação
* Empresas
* Usuários
* Perfis e Permissões
* Dashboard
* Clientes
* Produtos
* Categorias
* Estoque
* Pedidos
* Financeiro
* Relatórios
* Configurações

---

# Requisitos Funcionais

## RF001 - Autenticação

O sistema deve permitir:

* Cadastro de usuários.
* Login utilizando e-mail e senha.
* Logout.
* Recuperação de senha.
* Redefinição de senha.
* Renovação da sessão através de Refresh Token.
* Alteração de senha pelo usuário autenticado.

---

## RF002 - Empresas

O sistema deve permitir:

* Criar empresas.
* Editar empresas.
* Desativar empresas.
* Visualizar empresas.
* Alterar a empresa ativa.
* Definir o proprietário da empresa.

---

## RF003 - Usuários

O sistema deve permitir:

* Convidar usuários para uma empresa.
* Remover usuários da empresa.
* Editar informações do usuário.
* Ativar ou desativar usuários.
* Atualizar foto de perfil.
* Atualizar dados pessoais.

---

## RF004 - Perfis e Permissões

O sistema deve permitir:

* Criar perfis.
* Editar perfis.
* Excluir perfis.
* Associar permissões aos perfis.
* Associar perfis aos usuários.
* Controlar acesso às funcionalidades.

---

## RF005 - Dashboard

O sistema deve apresentar:

* Quantidade de clientes.
* Quantidade de produtos.
* Quantidade de pedidos.
* Receita.
* Despesas.
* Fluxo de caixa.
* Indicadores gerais da empresa.

---

## RF006 - Clientes

O sistema deve permitir:

* Cadastrar clientes.
* Editar clientes.
* Excluir clientes.
* Pesquisar clientes.
* Vincular endereços.
* Vincular contatos.
* Registrar observações.

---

## RF007 - Produtos

O sistema deve permitir:

* Cadastrar produtos.
* Editar produtos.
* Excluir produtos.
* Definir categoria.
* Definir preço.
* Definir custo.
* Gerenciar imagens.
* Definir estoque mínimo.

---

## RF008 - Categorias

O sistema deve permitir:

* Criar categorias.
* Editar categorias.
* Excluir categorias.
* Associar categorias aos produtos.

---

## RF009 - Estoque

O sistema deve permitir:

* Registrar entradas.
* Registrar saídas.
* Consultar saldo.
* Consultar movimentações.
* Ajustar estoque manualmente.

---

## RF010 - Pedidos

O sistema deve permitir:

* Criar pedidos.
* Adicionar produtos ao pedido.
* Alterar status do pedido.
* Calcular valores.
* Registrar descontos.
* Cancelar pedidos.

---

## RF011 - Financeiro

O sistema deve permitir:

* Registrar receitas.
* Registrar despesas.
* Categorizar lançamentos.
* Consultar fluxo de caixa.
* Filtrar lançamentos por período.

---

## RF012 - Relatórios

O sistema deve permitir:

* Exportar dados em CSV.
* Exportar dados em PDF.
* Filtrar informações.
* Gerar relatórios por período.

---

## RF013 - Configurações

O sistema deve permitir:

* Alterar informações da empresa.
* Configurar preferências do usuário.
* Configurar idioma.
* Configurar fuso horário.

---

# Requisitos Não Funcionais

## RNF001

O backend deverá ser desenvolvido utilizando Node.js e TypeScript.

## RNF002

O frontend deverá ser desenvolvido utilizando Next.js e TypeScript.

## RNF003

O banco de dados deverá ser PostgreSQL.

## RNF004

O sistema deverá utilizar autenticação baseada em JWT.

## RNF005

Todas as APIs deverão retornar respostas padronizadas.

## RNF006

O sistema deverá possuir tratamento centralizado de erros.

## RNF007

Todas as alterações no banco deverão ser realizadas através de Migrations.

## RNF008

O código deverá seguir padrões de organização definidos pela arquitetura do projeto.

---

# Fora do Escopo da Versão 1.0

As funcionalidades abaixo poderão ser implementadas em versões futuras:

* Chat interno.
* Notificações em tempo real.
* WebSockets.
* Multi-idioma.
* Integração com APIs externas.
* Emissão de notas fiscais.
* Aplicativo mobile.
* Integração com gateways de pagamento.
* Importação de planilhas.
* Filas de processamento.
