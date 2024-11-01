# Desafio de Criação de Dashboard com Power BI e DAX

Este projeto envolve a construção de um dashboard no Power BI, utilizando um modelo em estrela e várias funcionalidades DAX para análise de dados. O objetivo foi desenvolver um painel de controle dinâmico e interativo que facilite a visualização de informações importantes sobre vendas e desempenho de produtos ao longo do tempo.

## Estrutura e Processo de Construção do Diagrama

1. **Modelagem e Diagrama de Relacionamento**:
   - Primeiramente, criamos um **modelo estrela** no Power BI, onde organizamos as tabelas em duas categorias principais:
     - **Tabelas Fato**: Contêm dados transacionais, como `F_Vendas`, que registra cada venda feita.
     - **Tabelas Dimensão**: Representam entidades relacionadas, como `D_Calendário`, `D_Produtos`, e `D_Localização`.
   - **Relacionamentos** foram definidos entre as tabelas para facilitar a consulta e cruzamento de dados:
     - `F_Vendas` foi conectada à `D_Calendário` pela coluna `Date`.
     - A `D_Produtos` foi relacionada a `F_Vendas` pela coluna `ProductID`, e assim por diante.

2. **Construção da Tabela de Calendário**:
   - Utilizamos a função `CALENDAR()` para criar a tabela `D_Calendário`, que permite análises temporais flexíveis.
   - Fórmula utilizada:
     ```DAX
     D_Calendário = CALENDAR(MIN(F_Vendas[Date]), MAX(F_Vendas[Date]))
     ```
   - Colunas adicionais foram criadas para permitir uma análise detalhada por períodos específicos, usando funções DAX como `YEAR()`, `MONTH()`, `DAY()`, `WEEKDAY()`, etc.

3. **Criação de Medidas com DAX**:
   - **Vendas Totais**:
     Para calcular o total de vendas, utilizamos a função `SUM()`:
     ```DAX
     Total_Vendas = SUM(F_Vendas[SalesAmount])
     ```
   - **Unidades Vendidas**:
     Para somar as unidades vendidas, usamos `SUM` em `UnitsSold`:
     ```DAX
     Unidades_Vendidas = SUM(F_Vendas[UnitsSold])
     ```
   - **Média de Vendas por Produto**:
     A média de vendas por produto foi calculada usando `AVERAGE()` em `UnitsSold`:
     ```DAX
     Media_Unidades_Por_Produto = AVERAGE(F_Vendas[UnitsSold])
     ```

4. **Visualizações Criadas no Dashboard**:
   - **Gráficos de Linha e Barra**: Utilizados para visualizar as vendas e lucro ao longo do tempo e por categoria.
   - **Gráfico de Mapa**: Criado para mostrar a distribuição geográfica das vendas e do lucro.
   - **Gráficos de Torta e Donut**: Usados para mostrar as proporções das vendas e lucros entre diferentes segmentos e produtos.
   - **Tabela Dinâmica**: Para detalhar as vendas por período e categoria.

5. **Conclusão**:
   O projeto permitiu a criação de um painel de controle que oferece uma visão geral completa das vendas e do desempenho do negócio em múltiplas dimensões. Utilizando funções DAX e uma estrutura de modelo estrela, o dashboard facilita a exploração dos dados e a identificação de tendências e insights importantes.

