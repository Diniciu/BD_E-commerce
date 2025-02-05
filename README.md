# Banco de Dados - E-commerce Fictício

## 📋 Visão Geral

Este banco de dados foi projetado para um sistema de **e-commerce fictício**, com o objetivo de gerenciar informações sobre **produtos, pedidos, clientes, fornecedores, pagamentos e entregas**. O modelo é do tipo **relacional**, utilizando **SQL** para manipulação de dados. Ele é ideal para aplicações que exigem integridade referencial e transações consistentes, sendo aplicável tanto em ambientes de desenvolvimento quanto em produção.

## 🗂️ Estrutura do Banco de Dados

### 1️⃣ Tabelas Principais

- **`Produto`**
  - `idProduto` (INT): Identificador único do produto.
  - `Categoria` (VARCHAR(45)): Categoria do produto.
  - `Descrição` (VARCHAR(45)): Descrição detalhada do produto.
  - `Valor` (VARCHAR(45)): Preço do produto.

- **`Pedido`**
  - `idPedido` (INT): Identificador único do pedido.
  - `Status do Pedido` (VARCHAR(45)): Status atual do pedido (Ex: 'Pendente', 'Em andamento', 'Concluído').
  - `Descrição` (VARCHAR(45)): Detalhes do pedido.
  - `Cliente_idCliente` (INT): Referência ao cliente que realizou o pedido.
  - `Frete` (FLOAT): Valor do frete associado ao pedido.

- **`Cliente`**
  - `idCliente` (INT): Identificador único do cliente.
  - `Nome` (VARCHAR(45)): Nome do cliente.
  - `Identificação` (VARCHAR(45)): Documento de identificação (CPF/CNPJ).
  - `Endereço` (VARCHAR(45)): Endereço do cliente.

### 2️⃣ Tabelas de Relacionamento

- **`Relação de Produto/Pedido`**
  - `Produto_idProduto` (INT): Referência ao produto.
  - `Pedido_idPedido` (INT): Referência ao pedido.
  - `Quantidade` (VARCHAR(45)): Quantidade do produto no pedido.

- **`Produto_Estoque`**
  - `Produto_idProduto` (INT): Referência ao produto.
  - `Estoque_idEstoque` (INT): Referência ao estoque.
  - `Quantidade` (INT): Quantidade do produto em estoque.

### 3️⃣ Tabelas de Suporte

- **`Fornecedor`**
  - `idFornecedor` (INT): Identificador único do fornecedor.
  - `Razão Social` (VARCHAR(45)): Nome da empresa fornecedora.
  - `CNPJ` (VARCHAR(45)): CNPJ do fornecedor.
  - `Local` (VARCHAR(45)): Localização do fornecedor.

- **`Pagamento`**
  - `idPagamento` (INT): Identificador único do pagamento.
  - `Data de Validade` (VARCHAR(45)): Data de validade do cartão.
  - `Bandeira` (VARCHAR(45)): Bandeira do cartão (Visa, MasterCard, etc).
  - `Nome no Cartão` (VARCHAR(45)): Nome impresso no cartão.
  - `Cliente_idCliente` (INT): Referência ao cliente.

- **`Entrega`**
  - `idEntrega` (INT): Identificador único da entrega.
  - `Status de Entrega` (VARCHAR(45)): Status atual da entrega (Ex: 'Aguardando envio', 'Em trânsito', 'Entregue').
  - `Código de Rastreio` (VARCHAR(45)): Código de rastreamento da entrega.
  - `Pedido_idPedido` (INT): Referência ao pedido.

### 4️⃣ Outras Entidades

- **`Cliente PJ/PF`**
  - `idCliente PJ/PF` (INT): Identificador do cliente pessoa jurídica ou física.
  - `Email` (VARCHAR(45)): E-mail de contato.
  - `Pedido_idPedido` (INT): Referência ao pedido associado.

- **`Terceiro - Vendedor`**
  - `idTerceiro` (INT): Identificador do vendedor terceirizado.
  - `Razão Social` (VARCHAR(45)): Nome da empresa vendedora.
  - `Local` (VARCHAR(45)): Localização do vendedor.

- **`Disponibilizando Produto`**
  - `Fornecedor_idFornecedor` (INT): Referência ao fornecedor.
  - `Produto_idProduto` (INT): Referência ao produto disponibilizado.

## 🔗 Relacionamentos

- **1:N (Um para Muitos):**
  - Um cliente pode ter vários pedidos.
  - Um pedido pode ter vários pagamentos.
  - Um pedido pode ter várias entregas.

- **N:M (Muitos para Muitos):**
  - Um produto pode estar em vários pedidos e um pedido pode conter vários produtos.
  - Um produto pode estar em vários estoques e um estoque pode conter vários produtos.
  - Um fornecedor pode fornecer vários produtos e um produto pode ter vários fornecedores.

## 📊 Considerações Finais

Este modelo oferece uma base sólida para um sistema de e-commerce, permitindo expansões futuras, como integração com APIs de pagamento, sistemas de logística e análises de dados para insights de negócios.

**Boas práticas para implementação:**
- Utilização de índices em colunas de chaves estrangeiras para otimizar as consultas.
- Criação de triggers para garantir a integridade dos dados em operações críticas.
- Normalização das tabelas para evitar redundância de dados.

---
