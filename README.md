# 📊 Sales Forecast com Microsoft Fabric

Projeto end-to-end de previsão de vendas utilizando Microsoft Fabric (Lakehouse + Warehouse), modelagem dimensional em SQL e visualização estratégica no Power BI.

## 🔗 Dashboard publicado:
Visualizar Dashboard

## 🔗 Documentação (GitHub Pages):
https://opusvix.github.io/sales-forecast-powerbi/

## 🔗 Repositório:
https://github.com/opusvix/sales-forecast-powerbi

## 🎯 Contexto do Projeto

Empresas que trabalham com metas comerciais precisam prever vendas futuras para:

- Planejamento de estoque

- Definição de metas

- Projeção de receita

- Apoio à tomada de decisão estratégica

O objetivo deste projeto foi construir uma arquitetura analítica moderna, utilizando Microsoft Fabric, capaz de:

✔ Consolidar dados históricos

✔ Criar modelo dimensional confiável

✔ Implementar cálculo de forecast

✔ Disponibilizar visualização comparativa entre Realizado vs Previsto


## 🏗 Arquitetura da Solução

Pipeline implementado:

Lakehouse → Warehouse → Modelagem SQL → Power BI → GitHub Pages

🔹 Lakehouse

Armazenamento inicial dos dados brutos.

🔹 Warehouse

Camada estruturada para modelagem analítica e aplicação de regras de negócio.

🔹 SQL

Criação de tabelas dimensionais e fato.

🔹 Power BI

Visualização comparativa e construção das métricas.

## 📦 Modelagem de Dados

Foi adotado modelo dimensional simplificado:

## 🗂 dim_date

Tabela calendário criada via SQL para garantir:

- Padronização temporal

- Agrupamento mensal

- Criação de chave YearMonthKey

- Controle de ordenação no eixo do gráfico

Campos principais:

- date

- year

- month

- day_of_week

- is_weekend

- YearMonth

- YearMonthKey

## 🗂 fact_sales

Tabela fato contendo:

- date

- total_sales

- forecast_value

Relacionamento:

fact_sales.date → dim_date.date

## 🧠 Lógica de Forecast

O forecast foi calculado no Warehouse utilizando SQL com base em tendência histórica mensal.

Arquivo:

sql/forecast_query.sql

Estratégia aplicada:

- Agregação mensal

- Cálculo de média/tendência

- Projeção para períodos futuros

- Integração com modelo dimensional

## 📊 Dashboard

O dashboard apresenta:

- Linha de Vendas Reais

- Linha de Forecast

- Linha Total Forecast consolidada

- Comparação mensal

- Eixo ordenado por YearMonthKey

## 🛠 Medidas DAX

Exemplo de medidas utilizadas:

Total Sales = SUM(fact_sales[total_sales])


Total Forecast = SUM(fact_sales[forecast_value])

Arquivo com medidas:

powerbi/measures-dax.md

## 🚧 Desafios Técnicos Enfrentados

Durante o desenvolvimento foram resolvidos problemas como:

- Conflito de ordenação no eixo do Power BI

- Necessidade de chave YearMonthKey para ordenação correta

- Integração entre Lakehouse e Warehouse

- Tratamento de datas para garantir consistência temporal

- Estruturação do projeto para publicação no GitHub Pages

Esses ajustes garantiram:

✔ Escalabilidade

✔ Governança

✔ Padronização de modelo


## 📂 Estrutura do Repositório

sql/              → Scripts de criação e transformação

powerbi/          → Arquivo .pbip e medidas DAX

docs/             → Documentação do projeto (GitHub Pages)

docs/images/      → Imagens do projeto

data-model/       → Diagrama do modelo

## 🚀 Tecnologias Utilizadas

- Microsoft Fabric

- Lakehouse

- Warehouse SQL

- Power BI (.PBIP)

- DAX

- GitHub

- GitHub Pages

## 📈 Possíveis Evoluções

- Implementar modelo de regressão linear

- Aplicar Machine Learning automatizado

- Criar forecast por categoria/região

- Implementar CI/CD para versionamento de BI

- Automatizar ingestão via Dataflow Gen2

## 👨‍💻 Autor

Maurício Barros

Data Analytics | BI | Machine Learning

GitHub: https://github.com/opusvix

LinkedIn: https://www.linkedin.com/in/mauriciodasilvabarros/
