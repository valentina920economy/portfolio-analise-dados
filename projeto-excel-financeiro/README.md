# Automação de Controle Financeiro (Excel)

## Contexto
Planilha de controle de gastos pessoais com estrutura multi-abas, pensada para uso recorrente: lançamento diário de gastos e acompanhamento automático do orçamento por categoria.

## Metodologia
- Aba **Lançamentos**: registro de gastos com validação de dados (lista suspensa de categorias) e painéis congelados para facilitar o preenchimento contínuo
- Aba **Orçamento**: comparação automática entre valor orçado e gasto real por categoria, usando `SOMASE` (SUMIF) para puxar os dados da aba de lançamentos
- Cálculo de saldo restante e percentual utilizado por categoria
- Dashboards com gráfico de pizza (distribuição do gasto real) e gráfico de barras (orçado vs. realizado), atualizados automaticamente conforme novos lançamentos são inseridos

## Resultados
- Zero erros de fórmula (validado com recálculo automático)
- Painel 100% dinâmico: qualquer gasto novo lançado atualiza saldo, percentual e os dois gráficos sem intervenção manual

## Ferramentas
Excel (fórmulas SOMASE/SUMIF, validação de dados, gráficos dinâmicos, painéis congelados)

## Arquivo
`automacao-financeira-excel.xlsx` — modelo com dados fictícios de exemplo (as duas primeiras linhas de lançamento); basta apagar os exemplos e começar a preencher

## Nota
Este é um modelo genérico construído a partir de um projeto real de controle financeiro pessoal — os dados aqui são fictícios para preservar a privacidade da situação original.
