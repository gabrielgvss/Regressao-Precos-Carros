# MLPrecosAutomotivos

> Projeto de Machine Learning para análise e previsão de preços de veículos automotivos, utilizando dados limpos e estruturados, com foco em análise exploratória e preparação para modelagem.

## Estrutura do Projeto

- **notebooks/EDA.ipynb**: Notebook principal de Análise Exploratória de Dados (EDA).
- **dados/processed/car_price_dataset_clean.csv**: Base de dados limpa utilizada nas análises.

## Etapas Realizadas

### 1. Entendimento dos Dados

- Importação dos dados e bibliotecas essenciais.
- Dicionário de dados detalhado, com explicação de cada coluna (Brand, Model, Year, Engine_Size, Fuel_Type, Transmission, Mileage, Doors, Owner_Count, Price).

### 2. Análise Univariada

- Criação de funções para análise estatística de variáveis qualitativas e quantitativas.
- Análise de distribuição das principais variáveis:
  - **Brand**: Distribuição equilibrada entre as marcas, sem predominância excessiva.
  - **Model**: 29 modelos analisados, com distribuição também balanceada.
  - **Year**: Leve desbalanceamento, com predominância de veículos da década de 2010 e menor quantidade dos anos 2020.
  - **Engine_Size**: Análise detalhada por categorias, com destaque para veículos acima de 2.5L, que representam mais de 64% do total.
- Visualizações: gráficos de barras, histogramas, boxplots e gráficos de pizza para melhor compreensão das distribuições.
- Cálculo de diferenças e proporções entre categorias mais e menos frequentes para avaliar o balanceamento dos dados.

### 3. Considerações para Modelagem

- Discussão sobre possíveis impactos do desbalanceamento de algumas variáveis (como Year e Engine_Size) na modelagem.
- Sugestões de feature engineering, como criação da variável "idade do veículo".
- Recomendações para tratamento de variáveis categóricas e quantitativas em etapas futuras de Machine Learning.

## Próximos Passos

- Análise bivariada e multivariada para identificar relações entre variáveis.
- Preparação dos dados para modelagem (feature engineering, encoding, normalização).
- Construção e avaliação de modelos de regressão para previsão de preços.
- Interpretação dos resultados e ajustes conforme necessário.

## Como Executar

1. Clone este repositório.
2. Certifique-se de ter Python 3.8+ e as bibliotecas listadas no notebook instaladas.
3. Execute o notebook `notebooks/EDA.ipynb` para reproduzir as análises.

## Observações

- O projeto está em andamento, atualmente na etapa de análise exploratória.
- Novas etapas e melhorias serão adicionadas conforme o avanço do projeto.

---
