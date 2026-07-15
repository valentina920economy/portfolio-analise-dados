# Carteira de Investimentos — Perfil Conservador

## Contexto
Projeto acadêmico de montagem e acompanhamento de uma carteira hipotética de R$ 100.000, com perfil de investidor conservador, dividida entre renda fixa (Tesouro Selic, CDB, LCI) e renda variável (BBSE3, GGBR4).

## Metodologia
- Cálculo de rentabilidade líquida por ativo, considerando IR (tabela regressiva) e isenção fiscal da LCI
- Cálculo de retorno consolidado da carteira no período
- Desvio-padrão (volatilidade) semanal e anualizado dos ativos de renda variável
- Correlação de Pearson entre BBSE3 e GGBR4
- Comparação de eficiência entre produtos de renda fixa isentos e tributados

## Resultados
- Retorno total da carteira no período: ~3,9% (~4,1% considerando dividendos pendentes de GGBR4)
- Baixa correlação entre os dois ativos de renda variável (ρ ≈ 0,10), reforçando a diversificação
- LCI (95% do CDI, isenta de IR) superou o CDB 100% CDI líquido de imposto

## Ferramentas
Python (cálculo puro, sem bibliotecas externas)

## Arquivo
`carteira-investimentos.ipynb` — notebook com todos os cálculos, do zero até o retorno consolidado
