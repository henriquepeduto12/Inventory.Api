# Inventory.Api

Projeto desenvolvido em .NET 8 para o controle de estoque de produtos perecíveis e não perecíveis.

O sistema permite cadastrar produtos, registrar movimentações de entrada e saída, validar as regras de negócio e gerar relatórios com base nas informações do estoque.  
Foi utilizado Entity Framework Core com banco SQLite e Swagger para testes e documentação.

## Estrutura do Domínio

O sistema possui duas entidades principais: **Produto** e **Movimentação de Estoque**.

Cada produto possui:
- Código SKU (único)
- Nome
- Categoria (PERECIVEL ou NAO_PERECIVEL)
- Preço unitário
- Quantidade mínima em estoque
- Quantidade atual
- Data de criação

As movimentações de estoque estão ligadas a um produto e possuem:
- Tipo (ENTRADA ou SAIDA)
- Quantidade movimentada
- Data da movimentação
- Lote e data de validade (quando o produto é perecível)

## Regras de Negócio

- Produtos perecíveis devem ter lote e data de validade.  
- Não é permitido registrar movimentação com quantidade negativa.  
- Saídas só podem ser feitas se houver estoque suficiente.  
- Produtos com quantidade abaixo do mínimo devem gerar alerta.  
- Produtos perecíveis não podem ter movimentações após o vencimento.  
- O saldo do produto é atualizado automaticamente a cada movimentação.

## Relatórios

A API gera três relatórios principais:
1. Valor total do estoque (quantidade x preço unitário)
2. Produtos abaixo da quantidade mínima
3. Produtos perecíveis que vencem em até 7 dias

## Como Executar o Projeto

1. Clonar o repositório:

git clone https://github.com/henriquepeduto12/Inventory.Api.git
cd Inventory.Api

2. Executar o projeto:

dotnet run


## Endpoints Principais

- `POST /api/products` - Cadastra um novo produto  
- `POST /api/movements` - Registra uma movimentação (entrada ou saída)  
- `GET /api/reports/total-value` - Mostra o valor total do estoque  
- `GET /api/reports/below-minimum` - Mostra produtos abaixo da quantidade mínima  
- `GET /api/reports/expiring-7-days` - Mostra produtos que vencem em até 7 dias

## Entrega

Commits realizados conforme solicitado:
- Etapa 1 - Modelagem do domínio  
- Etapa 2 - Implementação das regras de negócio  
- Etapa 3 - Validações e tratamento de erros  
- Etapa final - Documentação e entrega  

Tag final criada: versao-final



