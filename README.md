Etapas do Projeto
Carregamento dos Dados

A tabela original, Financial Sample, foi importada como Financials_origem (em modo oculto, para backup).
Criação das Tabelas Dimensão As dimensões foram construídas agrupando, transformando ou derivando colunas da tabela original, conforme especificado:

D_Produtos

Contém dados agregados relacionados aos produtos.
Colunas: ID_produto, Produto, Média de Unidades Vendidas, Média do Valor de Vendas, Mediana do Valor de Vendas, Valor Máximo de Venda, Valor Mínimo de Venda.
Criada utilizando GROUP BY e DAX (ex.: funções como AVERAGE, MEDIAN, MAX, MIN).
D_Produtos_Detalhes

Contém informações detalhadas dos produtos.
Colunas: ID_produto, Discount Band, Sale Price, Units Sold, Manufactoring Price.
Relaciona produtos com detalhes operacionais.
D_Descontos

Contém informações relacionadas aos descontos.
Colunas: ID_produto, Discount, Discount Band.
Criada a partir de filtro e agrupamento.
D_Detalhes

Contém informações que não foram cobertas pelas outras tabelas.
Colunas adicionais identificadas como úteis para análises, como: Segment, Country, Salers.
D_Calendário

Criada com a função DAX CALENDAR() para gerar um calendário completo com granularidade diária.
Inclui: Date, Year, Month, Quarter, Day of Week.
Criação da Tabela Fato

F_Vendas
Representa as métricas de vendas detalhadas, conectando as tabelas dimensão.
Colunas:
SK_ID (Surrogate Key), ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Salers, Profit, Date.
Modelagem do Star Schema

As tabelas fato e dimensão foram relacionadas no Power BI utilizando chaves primárias e estrangeiras.
O esquema em estrela foi configurado para garantir alta performance nas análises.



Segue uma sugestão de estrutura e organização para atender ao desafio de projeto:

Descrição do Processo de Construção do Star Schema
O objetivo deste desafio é criar um modelo dimensional (Star Schema) utilizando a tabela única "Financial Sample". O processo consiste na separação das informações em tabelas fato e dimensão, para otimizar análises e relatórios no Power BI.

Etapas do Projeto
Carregamento dos Dados

A tabela original, Financial Sample, foi importada como Financials_origem (em modo oculto, para backup).
Criação das Tabelas Dimensão As dimensões foram construídas agrupando, transformando ou derivando colunas da tabela original, conforme especificado:

D_Produtos

Contém dados agregados relacionados aos produtos.
Colunas: ID_produto, Produto, Média de Unidades Vendidas, Média do Valor de Vendas, Mediana do Valor de Vendas, Valor Máximo de Venda, Valor Mínimo de Venda.
Criada utilizando GROUP BY e DAX (ex.: funções como AVERAGE, MEDIAN, MAX, MIN).
D_Produtos_Detalhes

Contém informações detalhadas dos produtos.
Colunas: ID_produto, Discount Band, Sale Price, Units Sold, Manufactoring Price.
Relaciona produtos com detalhes operacionais.
D_Descontos

Contém informações relacionadas aos descontos.
Colunas: ID_produto, Discount, Discount Band.
Criada a partir de filtro e agrupamento.
D_Detalhes

Contém informações que não foram cobertas pelas outras tabelas.
Colunas adicionais identificadas como úteis para análises, como: Segment, Country, Salers.
D_Calendário

Criada com a função DAX CALENDAR() para gerar um calendário completo com granularidade diária.
Inclui: Date, Year, Month, Quarter, Day of Week.
Criação da Tabela Fato

F_Vendas
Representa as métricas de vendas detalhadas, conectando as tabelas dimensão.
Colunas:
SK_ID (Surrogate Key), ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Salers, Profit, Date.
Modelagem do Star Schema

As tabelas fato e dimensão foram relacionadas no Power BI utilizando chaves primárias e estrangeiras.
O esquema em estrela foi configurado para garantir alta performance nas análises.
Funcionalidades e Funções DAX Utilizadas
Funções DAX para Agregações e Medidas

AVERAGE(), MEDIAN(), MAX(), MIN() para calcular valores na D_Produtos.
SUMX() e CALCULATE() para criar medidas customizadas, como lucros e descontos totais.
Criação do Calendário

CALENDAR(MIN(Financials_origem[Date]), MAX(Financials_origem[Date])) para gerar a tabela D_Calendário.
Colunas Condicionais

Exemplos:
Índice de Produtos: Criado com base em condições como níveis de vendas ou margens de lucro usando IF().
Reorganização e Otimização

As colunas foram organizadas para manter consistência no modelo e facilitar a leitura das tabelas.
