# Análise de Hábitos de Compra na Instacart

Neste projeto, analisei uma base relacional da plataforma de entregas de supermercado **Instacart** (5 tabelas interligadas, somando mais de 478 mil pedidos e 4,5 milhões de itens) para identificar padrões de consumo, recorrência e perfil de compras dos clientes.

## Limpeza e Preparação dos Dados

Antes de cruzar as tabelas com **Python** e **Pandas**, tratei as inconsistências da base:

* **Pedidos duplicados:** Identifiquei e removi 15 registros duplicados exatos no histórico de pedidos (todos concentrados na quarta-feira às 2h da manhã, indicando falha pontual de registro).
* **Produtos sem nome:** Preenchi 1.258 nomes ausentes em `products` como `'Unknown'` (todos pertencentes ao corredor 100 e departamento 21, reservados para itens não catalogados).
* **Ordem no carrinho:** Substituí 836 valores nulos em `add_to_cart_order` pelo código `999` e converti a coluna para inteiro. Todos os casos ocorriam em carrinhos com mais de 64 itens (limite de rastreamento sequencial do sistema).
* **Primeiro pedido:** Mantive os 28.817 valores nulos em `days_since_prior_order`, pois correspondem exatamente ao primeiro pedido (`order_number == 1`) de cada cliente.

## Principais Resultados

* **Horário e dias de pico:** A maior parte das compras ocorre em horário comercial (entre 9h e 17h), com volume concentrado no **domingo (84.090 pedidos)** e na **segunda-feira (82.185 pedidos)**.
* **Frequência de retorno:** O intervalo médio entre compras é de **11,1 dias**, com dois picos claros de comportamento: clientes que compram semanalmente (a cada 7 dias) e clientes de compra mensal (30 dias).
* **Tamanho do carrinho:** Cada pedido contém, em média, **10,1 itens**, com a maior concentração entre 3 e 6 produtos por compra.
* **Preferência por produtos frescos e orgânicos:** Tanto no ranking geral quanto nos itens adicionados primeiro ao carrinho e nas recompras, frutas e vegetais orgânicos lideram com folga — com **Banana (66.050 pedidos)** e **Bag of Organic Bananas (53.297 pedidos)** no topo.
* **Taxa de recompra:** A média de itens recomprados por cliente é de **49,5%**, mostrando um equilíbrio entre clientes ocasionais (taxa 0%) e clientes recorrentes fiéis aos mesmos itens básicos.

## Arquivos e Ferramentas
* `instacart-customer-behavior-analysis.ipynb`: Notebook com todo o código de limpeza, cruzamento de tabelas (`merge`), análise exploratória e gráficos.
* **Stack:** Python 3, Pandas, Matplotlib e Jupyter Notebook.
