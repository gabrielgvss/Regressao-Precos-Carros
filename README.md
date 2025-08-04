# MLPrecosAutomotivos

> Projeto de Machine Learning para análise e previsão de preços de veículos automotivos, utilizando dados limpos e estruturados, com foco em análise exploratória detalhada, identificação de relações entre variáveis e preparação para modelagem preditiva.

## Estrutura do Projeto

-   **notebooks/EDA.ipynb**: Notebook principal de Análise Exploratória de Dados (EDA), contendo todas as análises univariadas, bivariadas e as conclusões iniciais.
-   **dados/processed/car_price_dataset_clean.csv**: Base de dados limpa e pré-processada utilizada em todas as análises.
-   **environment.yml**: Arquivo Conda para reprodução exata do ambiente de desenvolvimento, incluindo todas as dependências.

## Etapas Realizadas e Conclusões Chave

### 1. Entendimento dos Dados

-   Importação dos dados e bibliotecas essenciais (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`).
-   Dicionário de dados detalhado, com explicação de cada coluna (Brand, Model, Year, Engine_Size, Fuel_Type, Transmission, Mileage, Doors, Owner_Count, Price), garantindo clareza sobre o dataset.

### 2. Análise Univariada

-   Criação de funções reutilizáveis para análise estatística e visualização de variáveis qualitativas e quantitativas.
-   Análise aprofundada da distribuição das principais variáveis:
    * **Brand**: Distribuição equilibrada entre as marcas, sem predominância excessiva, sugerindo que a marca, por si só, pode não ser o fator mais discriminatório de preço.
    * **Model**: 29 modelos analisados, com distribuição balanceada.
    * **Year**: Predominância de veículos da década de 2010 e menor quantidade dos anos 2020. Esta assimetria será considerada na modelagem.
    * **Engine_Size**: Destaque para veículos acima de 2.5L, que representam mais de 64% do total, indicando uma concentração em motores de maior cilindrada.
-   Visualizações abrangentes (gráficos de barras, histogramas, boxplots e gráficos de pizza) para melhor compreensão das distribuições.
-   Cálculo de diferenças e proporções entre categorias para avaliar o balanceamento e a representatividade dos dados.

### 3. Análise Bivariada

-   Foco na identificação de associações e correlações entre as variáveis preditoras e a variável alvo (`Price`).
-   **Para Variáveis Quantitativas (vs. Price):**
    * Cálculo de coeficientes de correlação de Pearson e Spearman e geração de scatter plots.
    * Identificadas as seguintes correlações significativas e de interesse para a modelagem, com indicativos de linearidade (coeficientes de Pearson e Spearman muito próximos):
        * **Year**: Correlação positiva forte (Pearson: 0.66). Carros mais novos tendem a ser mais caros.
        * **Mileage**: Correlação negativa moderada a forte (Pearson: -0.55). Maior quilometragem associada a preços menores.
        * **Engine_Size**: Correlação positiva moderada (Pearson: 0.36). Motores maiores tendem a associar-se a preços mais altos.
    * As variáveis `Doors` e `Owner_Count` não apresentaram correlação linear significativa com `Price` e, portanto, não serão incluídas no modelo inicial.

-   **Para Variáveis Categóricas (vs. Price):**
    * Análise visual via boxplots e confirmação estatística via teste ANOVA, seguida de testes Post-Hoc (Tukey HSD) para detalhamento das diferenças.
    * **Fuel_Type**:
        * O boxplot e o teste ANOVA indicaram uma associação estatisticamente significativa com `Price` (p-valor muito baixo).
        * O teste Post-Hoc de Tukey HSD revelou que carros **Elétricos** e **Híbridos** são **significativamente mais caros** do que carros a Diesel e a Gasolina. Carros **Elétricos** também são mais caros que **Híbridos**. Não foi encontrada diferença significativa entre preços de carros a Diesel e a Gasolina.
    * **Transmission**:
        * O boxplot e o teste ANOVA indicaram uma associação estatisticamente significativa com `Price` (p-valor muito baixo).
        * O teste Post-Hoc de Tukey HSD demonstrou que carros com transmissão **Automática** são **significativamente mais caros** do que carros com transmissão Manual e Semi-Automática. Não há diferença estatisticamente significativa nos preços médios entre carros com transmissão Manual e Semi-Automática.
    * As variáveis `Brand` e `Model` não demonstraram associação significativa com `Price` via teste ANOVA e, portanto, não serão incluídas no modelo inicial.

### 4. Considerações para Modelagem

-   Com base na análise bivariada, as seguintes variáveis foram identificadas como **preditores essenciais** para o modelo de regressão: `Year`, `Mileage`, `Engine_Size`, `Fuel_Type` e `Transmission`.
-   Variáveis como `Brand`, `Model`, `Doors` e `Owner_Count` não serão incluídas no modelo de regressão linear múltipla inicial, devido à ausência de associação significativa na análise bivariada, visando a parsimônia e interpretabilidade do modelo.
-   Para as variáveis categóricas selecionadas (`Fuel_Type` e `Transmission`), será necessário realizar a codificação (e.g., One-Hot Encoding ou variáveis dummy) antes da modelagem.
-   A criação de variáveis de `idade do veículo` (derivada de `Year`) pode ser explorada como uma técnica de feature engineering.

## Próximos Passos

-   **Análise Multivariada e Construção do Modelo de Regressão:**
    * Desenvolvimento de um modelo de regressão linear múltipla utilizando as variáveis preditoras identificadas.
    * Verificação de pressupostos do modelo (linearidade, normalidade dos resíduos, homoscedasticidade, ausência de multicolinearidade).
    * Interpretação dos coeficientes do modelo e sua significância estatística.
    * Avaliação do desempenho do modelo (R-quadrado, RMSE, etc.).
-   **Validação do Modelo:**
    * Aplicação de técnicas de validação cruzada para garantir a robustez e generalização do modelo.
-   **Interpretação e Comunicação:**
    * Documentação detalhada dos resultados e insights obtidos para apoiar a tomada de decisões.

## Como Executar

1.  Clone este repositório.
2.  Certifique-se de ter Python 3.8+ e as bibliotecas listadas no `environment.yml` instaladas. É recomendado criar o ambiente Conda usando `conda env create -f environment.yml`.
3.  Ative o ambiente Conda (`conda activate seu_ambiente_aqui`).
4.  Execute o notebook `notebooks/EDA.ipynb` para reproduzir as análises.

## Observações

-   O projeto está em andamento, avançando da análise exploratória para a construção e avaliação de modelos preditivos.
-   Novas etapas e melhorias serão adicionadas conforme o avanço do projeto.
