# 🏠 House Prices – Modelagem de Regressão com Machine Learning

Este repositório contém um projeto completo de análise, pré-processamento, modelagem e avaliação de modelos de **Machine Learning para regressão**, utilizando o famoso dataset **House Prices – Advanced Regression Techniques** (Kaggle).  
O objetivo é prever o preço de venda de imóveis com base em suas características estruturais, de qualidade e localização.

---

## 📌 Sumário
- [Descrição do Projeto](#descrição-do-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Dataset](#dataset)
- [Etapas do Projeto](#etapas-do-projeto)
- [Modelos Avaliados](#modelos-avaliados)
- [Resultados Obtidos](#resultados-obtidos)
- [Análise dos Erros](#análise-dos-erros)
- [Como Executar](#como-executar)
- [Estrutura do Repositório](#estrutura-do-repositório)
- [Melhorias Futuras](#melhorias-futuras)
- [Licença](#licença)

---

## 📖 Descrição do Projeto

Este projeto aplica técnicas de **aprendizado supervisionado** para resolver o problema de regressão de previsão de preços de casas.

Foram realizadas:
- Análise exploratória dos dados (EDA)
- Pré-processamento completo com Pipelines e ColumnTransformer
- Transformação logarítmica da variável-alvo
- Treinamento de múltiplos modelos
- Avaliação comparativa com métricas e cross-validation
- Análise de resíduos e principais erros

---

## 🛠 Tecnologias Utilizadas

- Python 3.10+
- Pandas
- NumPy
- Matplotlib / Seaborn
- Scikit-learn
- SciPy
- Jupyter Notebook

---

## 🗂 Dataset

Dataset: **House Prices – Advanced Regression Techniques** (Kaggle)  
Contém:
- 1460 registros
- 79 variáveis preditoras
- Variável-alvo: `SalePrice`

O dataset deve ser baixado manualmente devido às regras do Kaggle:  
🔗 https://www.kaggle.com/c/house-prices-advanced-regression-techniques

---

## 🔎 Etapas do Projeto

### 1️⃣ Análise Exploratória (EDA)
- Estudo da distribuição da variável alvo  
- Correlações entre variáveis  
- Gráficos de dispersão, boxplots e heatmap  
- Verificação de outliers  
- Transformação `log1p` para reduzir assimetria

### 2️⃣ Pré-processamento com Pipelines
- Imputação de valores faltantes  
- Padronização de variáveis numéricas  
- Codificação **ordinal** para `KitchenQual`  
- Codificação **One-Hot** para variáveis nominais  
- Combinação de transformações via `ColumnTransformer`  
- Transformação do target com `TransformedTargetRegressor`

### 3️⃣ Treinamento dos Modelos
Modelos utilizados:
- **LinearRegression**
- **RandomForestRegressor**
- **KNeighborsRegressor**

### 4️⃣ Avaliação
Métricas:
- RMSE  
- MAE  
- R²  
- Cross-validation (KFold 5-fold)

---

## 📊 Resultados Obtidos

### 📌 Desempenho no Conjunto de Teste

| Modelo | RMSE ↓ | MAE ↓ | R² ↑ |
|-------|--------|--------|------|
| **Linear Regression** | **28.367** | 18.354 | **0.895** |
| Random Forest | 28.461 | **17.752** | 0.894 |
| KNN Regressor | 36.170 | 20.712 | 0.829 |

### 📌 Cross-Validation (5-fold)

- **RMSE médio:** 46.592  
- **Desvio padrão:** 40.018  

### 📌 Conclusões

- A **Regressão Linear** obteve o melhor equilíbrio geral entre RMSE e R².  
- O **Random Forest** apresentou o menor MAE, indicando bom desempenho para valores medianos.  
- O **KNN** foi prejudicado pela alta dimensionalidade resultante do One-Hot Encoding.  
- Todos os modelos apresentaram tendência a **subestimar imóveis muito valorizados** (alta cauda no QQ-plot).

---

## 🧪 Análise dos Erros

Foram avaliados:
- Distribuição dos resíduos  
- Resíduo vs Valor Predito  
- QQ-Plot para normalidade  
- Tabela de maiores erros absolutos  

Principais observações:
- Resíduos relativamente bem distribuídos em valores centrais  
- Heterocedasticidade para imóveis caros  
- Subestimação consistente de casas premium  
- Cauda longa demonstrada no QQ-plot

---
