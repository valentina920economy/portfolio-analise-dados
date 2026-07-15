# Análise Fatorial — Qualidade do Vinho

## Contexto
Projeto acadêmico de análise fatorial exploratória aplicado ao dataset público **Wine Quality (Red)**, do UCI Machine Learning Repository — 1.599 observações e 11 variáveis físico-químicas.

## Metodologia
- Padronização das variáveis (média = 0, desvio padrão = 1)
- Testes de adequação: esfericidade de **Bartlett** e **KMO** (Kaiser-Meyer-Olkin)
- **Refinamento de variáveis:** a análise inicial com as 11 variáveis apresentou KMO geral de 0,432 (inadequado). Removendo iterativamente a variável com menor KMO individual a cada passo (`residual sugar` → `alcohol` → `chlorides` → `total sulfur dioxide` → `free sulfur dioxide`), o KMO geral subiu para **0,680 (adequado)**, com as 6 variáveis remanescentes atingindo MSA individual ≥ 0,5
- Critério de Kaiser (autovalores > 1) para retenção de fatores, com rotação varimax

## Resultados

**Testes de adequação (solução final, 6 variáveis)**
- Bartlett: qui-quadrado = 3.974,04, p-valor < 0,001
- KMO geral = 0,680 (adequado)

**Fatores extraídos**
- **Fator 1 — Corpo/Acidez fixa (32,99% da variância):** cargas altas em `fixed acidity` (0,956) e `density` (0,680), com carga negativa em `pH` (-0,576) — eixo de acidez estrutural do vinho
- **Fator 2 — Acidez volátil vs. frescor (24,05% da variância):** oposição entre `volatile acidity` (-0,792) e `citric acid` (0,709) — tensão entre acidez associada a deterioração e acidez associada a frescor
- Variância total explicada pelos 2 fatores: **57,03%**

## Nota metodológica
A primeira tentativa, com as 11 variáveis originais, tinha variância explicada nominalmente maior (70,8%), mas estava construída sobre uma base estatisticamente inadequada (KMO = 0,432) — a correlação entre as variáveis estava concentrada em poucas delas, não distribuída o suficiente para sustentar uma boa solução fatorial. Refinar a seleção de variáveis até atingir KMO adequado prioriza validade estatística sobre variância explicada nominal.

## Ferramentas
Python, factor_analyzer, scikit-learn, pandas

## Arquivo
`analise-fatorial-vinho.ipynb`
