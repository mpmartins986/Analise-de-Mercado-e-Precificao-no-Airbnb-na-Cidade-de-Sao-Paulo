# 🏡 Análise de Mercado e Precificação no Airbnb

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![GeoPandas](https://img.shields.io/badge/GeoPandas-139C5A?style=flat&logo=geopandas&logoColor=white)](https://geopandas.org/)
[![Status](https://img.shields.io/badge/Status-Concluído-success)]()

Projeto de análise exploratória e geoespacial de dados ponta a ponta sobre o mercado do Airbnb. Este projeto abrange o tratamento de dados em Python, correção de formatações regionais de moeda e remoção de outliers extremos, seguido por mapeamento coroplético, análise da distribuição de preços por acomodação e avaliação de sazonalidade de reservas.

---

## 📊 Visão Geral do Mercado & Visualizações

### 1. Distribuição Espacial do Preço Mediano por Bairro
![Mapa de Preço Mediano](https://raw.githubusercontent.com/mpmartins986/Analise-de-Mercado-e-Precificao-no-Airbnb-na-Cidade-de-Sao-Paulo/main/mapa_precos_bairros.png)

### 2. Distribuição de Preço por Tipo de Acomodação
![Boxplot por Tipo de Quarto](https://raw.githubusercontent.com/mpmartins986/Analise-de-Mercado-e-Precificao-no-Airbnb-na-Cidade-de-Sao-Paulo/main/boxplot_room_type.png)

### 3. Volume de Avaliações & Sazonalidade de Reservas
![Sazonalidade das Avaliações](https://raw.githubusercontent.com/mpmartins986/Analise-de-Mercado-e-Precificao-no-Airbnb-na-Cidade-de-Sao-Paulo/main/sazonalidade_reviews.png)

---

## 🎯 Perguntas de Negócio & Insights

| Pergunta de Negócio | Abordagem Analítica | Conclusão / Ação de Negócio |
| :--- | :--- | :--- |
| **Como os preços variam pela cidade?** | Mapeamento coroplético unindo o arquivo `neighbourhoods.geojson` com a mediana agregada dos preços dos anúncios. | Disparidade espacial evidente pela cidade. Bairros nobres e centrais apresentam um valor significativamente superior às áreas periféricas, destacando zonas prioritárias para investimentos de maior rendimento. |
| **O que impulsiona o valor das diárias?** | Análise comparativa de distribuição via boxplots entre as categorias de `room_type`. | Imóveis inteiros (casas/apartamentos) concentram as faixas de preço mais altas e maior amplitude interquartil, enquanto quartos privativos e compartilhados se mantêm estáveis em faixas de menor custo. |
| **Existe sazonalidade na demanda?** | Série temporal mensal do total acumulado de avaliações dos hóspedes (`year_month`). | O volume de avaliações exibe picos cíclicos em períodos de férias e verão, sinalizando as melhores janelas para adoção de tarifas dinâmicas. |

---

## 🛠️ Tecnologias Utilizadas & Metodologia

* **Linguagem & Bibliotecas:** Python (`pandas`, `geopandas`, `matplotlib`, `seaborn`, `mapclassify`).
* **Limpeza e Pipeline de Dados:**
  * Limpeza de strings de texto com símbolos de moeda e conversão de preços para valores numéricos contínuos (`float64`).
  * Filtragem de anomalias de calendário e outliers extremos utilizando o corte pelo percentil 99 (**P99 ≈ R$ 1.911,50**), retendo mais de 41.000 anúncios válidos.
  * Extração de atributos temporais (ano-mês) das avaliações para analisar o volume de reservas ao longo do tempo.
  * Junção espacial (*spatial join*) entre as métricas dos anúncios e os limites vetoriais do arquivo GeoJSON.

---

## 📁 Estrutura do Repositório

* `listings.csv` / `listings_cleaned.csv`: Dados brutos e tratados dos anúncios.
* `reviews.csv` / `reviews_clean.csv`: Histórico de avaliações e variáveis temporais.
* `neighbourhoods.geojson`: Polígonos de fronteira dos bairros.
* `airbnb_visuals.ipynb`: Notebook Jupyter com o tratamento de dados, uniões geoespaciais e geração de gráficos.
* `mapa_precos_bairros.png`: Imagem exportada do mapa coroplético.
* `boxplot_room_type.png`: Gráfico exportado de distribuição de preços por tipo de acomodação.
* `sazonalidade_reviews.png`: Gráfico de linhas exportado sobre a sazonalidade de avaliações.

---

## 🚀 Como Executar Localmente

1. Clone este repositório:
```bash
git clone [https://github.com/SEU_USUARIO/airbnb-pricing-analytics.git](https://github.com/SEU_USUARIO/airbnb-pricing-analytics.git)
cd airbnb-pricing-analytics
