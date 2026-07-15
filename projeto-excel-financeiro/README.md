# Automação de Controle Financeiro (Excel)

## Contexto
Planilha de controle financeiro pessoal com estrutura multi-abas, cobrindo três frentes: acompanhamento mensal de renda e quitação de dívidas, registro diário de gastos por categoria, e um painel consolidado que calcula quanto sobra para investir. Dados fictícios, modelo construído a partir de um caso real de organização financeira pessoal, anonimizado para portfólio.

## Metodologia
- **10 abas mensais (Renda Julho → Renda Abril)**: acompanham renda, dívidas ativas e percentual da renda comprometida mês a mês, com o saldo devedor de um mês puxando automaticamente o saldo do mês anterior (fórmula encadeada entre abas)
- **Aba Gastos diários**: registro de lançamentos individuais (data, categoria, descrição, valor)
- **Aba Gastos totais**: painel consolidado que usa `SOMASE` (SUMIF) para somar os gastos de cada categoria a partir da aba de lançamentos, compara com o limite orçado, calcula a sobra e sinaliza com `SE` (IF) quando uma categoria estourou o orçamento
- **Valor para investimento**: célula final que soma o saldo líquido de todas as categorias (positivas e negativas) para indicar quanto está disponível para aplicar

## Resultados
- Zero erros de fórmula (validado com recálculo automático)
- Painel 100% dinâmico: qualquer gasto novo lançado atualiza automaticamente sobra, status e valor disponível para investimento
- Lógica condicional testada com um cenário real de estouro de orçamento (categoria "Assinaturas"), confirmando que o status "Negativo" responde corretamente aos dados

## Ferramentas
Excel (fórmulas SOMASE/SUMIF, SE, referências entre abas, validação de dados, painéis congelados)

## Arquivo
`controle-financeiro-generico.xlsx` — modelo com dados fictícios de renda, dívidas e gastos diários

## Nota
Este é um modelo genérico construído a partir de um projeto real de controle financeiro pessoal, tendo nomes, valores e descrições substituídos por dados fictícios para preservar a privacidade da situação original.
