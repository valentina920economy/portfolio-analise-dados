# Análise do Setor Vitivinícola do RS — SEFAZ-RS

## Contexto
Projeto acadêmico apresentado à Secretaria da Fazenda do Rio Grande do Sul (SEFAZ-RS) — Unisinos, Análise Econômica Setorial, 2026.

**Equipe:** Enzo Degrazia, Leonardo Rodrigues, Marcelo Dimas, Valentina Rodrigues e Volmir Júnior.

Análise completa da cadeia produtiva do setor vitivinícola do Rio Grande do Sul, estruturada em 6 eixos: matéria-prima, indústria, exportação, importação, impactos exógenos e arrecadação, com um modelo preditivo (SVR) simulando o impacto do Acordo Mercosul-UE sobre a competitividade do setor.

## Fontes de dados
IBGE, Comex Stat (MDIC), Receita Dados (SEFAZ-RS) e SGS (Banco Central do Brasil).

## Estrutura da análise

**01 · Matéria-prima** — Produção e preço da uva na Serra Gaúcha e no RS. O RS concentra ~81% da produção nacional de uva, com pico de 904.794 t em 2023 e queda de 24% em 2024 (686.651 t) após as enchentes. Cinco municípios (com destaque para Flores da Cunha) concentram mais de 65% da produção da Serra Gaúcha.

**02 · Indústria** — ~90% do vinho e suco de uva do Brasil é produzido no RS. A Cooperativa Aurora reúne mais de 1.100 famílias e processa 10-15% de toda a uva do estado. Uvas americanas (Isabel, Bordô) respondem por ~80% da produção (sucos e vinhos de mesa); uvas europeias (Merlot, Chardonnay, Cabernet) por ~20% (vinhos finos e espumantes, maior valor agregado).

**03 · Exportação** — O RS domina ~85% das exportações brasileiras de vinho. Valor exportado teve pico em 2022 (US$ 12,5 Mi FOB), caiu com as enchentes de 2024 e recuperou em 2025 (US$ 11,6 Mi). Preço médio de exportação: US$ 1,84/litro.

**04 · Importação e modelo preditivo (SVR)** — O Brasil importa majoritariamente do Chile (US$ 213 Mi em 2025, maior fornecedor), com preço médio de US$ 3,37/litro (França no segmento premium, US$ 9,27/litro).

Modelo SVR aplicado a diferentes NCMs do setor para simular o impacto do Acordo Mercosul-UE:

| NCM | Categoria | Impacto simulado | Classificação |
|---|---|---|---|
| 2204.10.90 | Outros espumantes | +17,37% | Anticíclico / substituição |
| 2204.22.11 | Vinhos de 2L a 10L | -0,40% | Consumo altamente inelástico |
| 2204.21.00 | Vinhos em embalagem < 2L | -7,28% | Vulnerabilidade moderada |
| 2204.29.10 | Vinhos a granel > 10L | -8,01% | Sensível à demanda industrial |
| 2204.10.10 | Espumante moscatel | -9,87% | Alta vulnerabilidade interna |

A simulação testou o acirramento da concorrência de vinhos finos europeus com a abertura do Acordo Mercosul-UE. O modelo identificou que os espumantes finos (NCM 2204.10.90) operam de forma **anticíclica**: diante da queda nas vendas em determinadas regiões, a indústria consegue direcionar a produção para outros estados e mercados externos, aumentando a receita.

**05 · Impactos exógenos** — Enchentes de 2024 (maior desastre climático do RS, safra caiu 24%), El Niño e míldio (aumento de chuvas favorece a principal doença da videira), e riscos adicionais como herbicida por deriva, urbanização e carga tributária.

**06 · Arrecadação** — O ICMS do vinho cresceu 76% entre 2015 e 2025 (R$ 156,9 Mi → R$ 277,2 Mi), representando 0,52% do total arrecadado pelo RS em 2025.

## Metodologia técnica do modelo SVR
- Tratamento de dados: conversão de encoding (ISO-8859-1 → UTF-8), limpeza de caracteres não numéricos
- Agregação mensal do câmbio (média aritmética); deflação do faturamento pelo IPCA acumulado (preços constantes)
- Normalização via StandardScaler (Z-score)
- Modelo: SVR com kernel RBF, epsilon = 0.1, C = 10.0
- Desempenho: R² = 0,9895 (~99% da variabilidade explicada), MAE ≈ R$ 2,75 milhões, RMSE ≈ R$ 3,06 milhões

## Conclusões
O RS é o principal produtor e exportador de vinho do Brasil, mas ainda exporta a preço médio bem abaixo do que importa (US$ 1,84/L vs. US$ 3,37/L), indicando espaço para valorização via indicações geográficas e inserção em mercados premium. O Acordo Mercosul-UE representa risco de concorrência assimétrica para vinhos de entrada, mas os espumantes gaúchos surgem como o segmento mais preparado para competir. A forte concentração regional (85% das exportações nacionais) também expõe o setor a choques climáticos localizados.

## Ferramentas
Python, Pandas, Scikit-learn
