# Modelos de Machine Learning aplicados a dados econômicos

Dois projetos aplicando técnicas de Machine Learning a problemas com dados reais, na disciplina de Análise Econômica com Machine Learning.

---

## 1. Clustering — Perfil econômico dos municípios do RS

**Autoria:** Leonardo Rodrigues e Valentina Rodrigues

**Objetivo:** Agrupar os municípios do Rio Grande do Sul por perfil de atividade econômica (Agropecuária, Indústria, Administração Pública, Outros Serviços), ano a ano entre 2013 e 2021, para identificar como a estrutura econômica regional evoluiu ao longo do tempo.

**Metodologia**
- Dados no formato wide (ano/variável em colunas) transformados para long, com extração de ano e variável via regex
- Tratamento de valores ausentes por mediana, agrupado por ano
- Padronização das variáveis (StandardScaler)
- Modelo: **Gaussian Mixture Model**, com número ótimo de clusters escolhido por ano via **BIC** (Bayesian Information Criterion)

**Resultados**
O número de clusters variou significativamente entre os anos — de 7 (2014, 2020) a 14 (2017), passando por 10, 11, 12 e 13 em outros anos. Essa oscilação indica que o perfil econômico dos municípios gaúchos **não é estático**: em alguns anos a diferenciação entre municípios se acentua, em outros se reduz — um padrão possivelmente associado a choques econômicos, climáticos ou políticos que afetam as regiões de forma desigual.

**Ferramentas:** Python, Pandas, Scikit-learn (GaussianMixture, StandardScaler)

---

## 2. SVR — Previsão de desempenho estudantil

**Base de dados:** Student Performance (UCI Machine Learning Repository) — Cortez & Silva (2008)

**Objetivo:** Prever a nota final (G3, escala 0-20) de estudantes do ensino secundário em Portugal a partir de características socioeconômicas e comportamentais — sem usar as notas parciais (G1, G2) como preditoras.

**Decisão metodológica central:** G1 e G2 têm correlação acima de 0.8 com G3. Incluí-las tornaria a previsão trivial e esconderia os fatores reais por trás do desempenho — por isso foram **excluídas propositalmente** das features, mantendo o modelo honesto sobre o que de fato explica a nota.

**Metodologia**
- Análise exploratória identificando variáveis mais associadas ao desempenho (aspiração de cursar ensino superior, reprovações anteriores)
- Label Encoding para variáveis categóricas
- Padronização com fit apenas no conjunto de treino (evitando data leakage)
- Comparação entre SVR com 3 kernels (linear, RBF, polinomial) e Regressão Linear (OLS)
- Otimização de hiperparâmetros (C, epsilon, gamma) via GridSearchCV com validação cruzada 5-fold
- Diagnóstico de resíduos e análise de erro por faixa de nota

**Resultados**

| Modelo | RMSE | MAE | R² |
|---|---|---|---|
| SVR Linear | 2,81 | 2,06 | 0,192 |
| SVR RBF | 2,80 | 2,02 | 0,195 |
| SVR Polinomial | 2,80 | 2,04 | 0,197 |
| **SVR RBF Otimizado** | **2,72** | **1,98** | **0,242** |
| Regressão Linear | 2,84 | 2,11 | 0,172 |

O SVR RBF otimizado via GridSearchCV superou todos os demais modelos, incluindo a Regressão Linear — confirmando a hipótese inicial de que a relação entre as variáveis e o desempenho estudantil é predominantemente não linear. A validação cruzada (5-fold) confirmou a estabilidade relativa desse resultado (RMSE 2,68 ± 0,23).

**Ferramentas:** Python, Pandas, Scikit-learn (SVR, GridSearchCV, LinearRegression)

---

## Arquivos
- `clustering-municipios-rs.ipynb`
- `svr-desempenho-estudantil.ipynb`
