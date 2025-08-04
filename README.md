# 📈 Projeto de Análise e Previsão de Preços de Veículos Automotivos

> Este projeto tem como objetivo aplicar técnicas de **Análise Exploratória de Dados (EDA)** e **Modelagem Estatística/Predição** para entender os fatores que mais influenciam o preço de veículos e construir modelos capazes de estimar esse valor com precisão. Ele se encaixa no universo de **Machine Learning supervisionado**, focado em **problemas de regressão**.

---

## 📁 Estrutura do Projeto

- **notebooks/EDA.ipynb**  
  Contém toda a exploração e análise dos dados, com visualizações, testes estatísticos e conclusões parciais.
  
- **dados/processed/car_price_dataset_clean.csv**  
  Base de dados tratada, limpa e estruturada, pronta para uso em análise e modelagem.

- **environment.yml**  
  Arquivo que define o ambiente Conda com todas as bibliotecas utilizadas, garantindo reprodutibilidade.

---

## 🔍 Etapas do Projeto

### 1. **Entendimento dos Dados**
- Importação da base e bibliotecas (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`, entre outras).
- Criação de um **dicionário de dados**, explicando o significado e tipo de cada coluna, como:  
  `Brand`, `Model`, `Year`, `Engine_Size`, `Fuel_Type`, `Transmission`, `Mileage`, `Doors`, `Owner_Count`, `Price`.

---

### 2. **Análise Univariada**
> Nessa etapa, observamos **cada variável individualmente** para entender sua distribuição, outliers e comportamento geral.

- Gráficos como **boxplots, histogramas, gráficos de barras e pizza** foram usados para visualizar tanto variáveis **numéricas quanto categóricas**.
- Exemplo de achados:
  - A maior parte dos carros tem motores acima de 2.5L.
  - A distribuição dos anos de fabricação é mais concentrada na década de 2010.
  - `Price` tem assimetria e valores extremos (carros muito caros e raros).

---

### 3. **Análise Bivariada**
> Aqui buscamos entender como **cada variável se relaciona com o preço**, uma de cada vez.

#### 🧮 Variáveis Numéricas × `Price`
- Usamos **correlação de Pearson e Spearman** + scatterplots.
- Achados principais:
  - `Year` tem correlação positiva **forte** com `Price` (0.66): quanto mais novo o carro, maior o preço.
  - `Mileage` tem correlação **negativa forte** (-0.55): quanto mais rodado, menor o preço.
  - `Engine_Size` tem correlação positiva **moderada** (0.36): motores maiores tendem a ser mais caros.
  - `Doors` e `Owner_Count` não mostraram correlação significativa → candidatos à exclusão do modelo.

#### 🧪 Variáveis Categóricas × `Price`
- Utilizamos **ANOVA** e **teste post-hoc de Tukey** para verificar se as categorias têm preços significativamente diferentes.
- Achados:
  - `Fuel_Type`: veículos **elétricos e híbridos** são mais caros que os demais (diferenças estatisticamente significativas).
  - `Transmission`: veículos **automáticos** são significativamente mais caros.
  - `Brand` e `Model` não mostraram associação significativa com o preço → podem ser descartadas do modelo inicial por questão de simplicidade.

---

### ✅ **Conclusão até o momento**
As variáveis **mais relevantes** para explicar o preço dos carros com base na análise bivariada foram:

- `Year`
- `Mileage`
- `Engine_Size`
- `Fuel_Type`
- `Transmission`

Essas serão usadas como **variáveis preditoras iniciais** na construção do modelo de regressão.

---

## 🔮 Próximos Passos: Análise Multivariada e Modelagem

### 🛠 O que será feito:
- Construção de um modelo de **Regressão Linear Múltipla** para verificar o impacto combinado das variáveis no preço.
- **Codificação de variáveis categóricas** (dummy/one-hot encoding) para uso no modelo.
- Verificação de **pressupostos estatísticos** da regressão:
  - Linearidade
  - Normalidade dos resíduos
  - Homoscedasticidade
  - Multicolinearidade

### 📈 Avaliação do Modelo:
- Métricas como **R² ajustado**, **AIC**, **RMSE**.
- Se necessário, comparação entre diferentes versões do modelo (com mais ou menos variáveis).
- Validação cruzada para garantir a **generalização dos resultados**.

---

## 💻 Como Executar

Você pode executar este projeto de duas formas: utilizando **Conda** (recomendado para garantir reprodutibilidade do ambiente) ou **pip** (caso prefira ambientes virtuais padrão do Python).

---

### ✅ 1. Usando Conda (recomendado)
1. Clone o repositório: `git clone https://github.com/seu-usuario/MLPrecosAutomotivos.git`

2. Crie o ambiente Conda com base no arquivo environment.yml:
   `conda env create -f environment.yml`
3. Ative o ambiente Conda:
   `conda activate ml_precos_automotivos`
4. Inicie o Jupyter Notebook:
   `jupyter notebook notebooks/EDA.ipynb`

