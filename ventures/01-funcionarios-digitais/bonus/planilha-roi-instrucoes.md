# Bônus 4 — Planilha de ROI: instruções de uso

A planilha de ROI responde, com números, a pergunta que vai aparecer na sua cabeça em algum domingo de preguiça: *"isso tudo está valendo a pena?"*. Preenchê-la leva 5 minutos por semana — de preferência no fim do bloco de sexta-feira (capítulo 9).

## Como importar no Google Sheets

1. Abra [sheets.google.com](https://sheets.google.com) e crie uma planilha em branco.
2. Menu **Arquivo → Importar → Fazer upload** e escolha o arquivo `planilha-roi.csv`.
3. Na tela de importação, em "Tipo de separador", escolha **Ponto e vírgula** (o arquivo usa o padrão brasileiro). Confirme.
4. Pronto. Renomeie para "ROI — Funcionários Digitais" e deixe nos favoritos.

> Prefere Excel? Basta abrir o CSV direto — o ponto e vírgula é o separador padrão do Excel em português.

## Como preencher cada coluna (5 min por semana)

- **Horas economizadas (Atendimento, Vendas, Conteúdo, Administrativo):** estimativa honesta de quanto tempo cada funcionário digital te poupou na semana, comparado com o jeito antigo (ou com a tarefa que simplesmente não era feita). Não precisa de cronômetro: pense em "quantas vezes usei resposta rápida × 3 min", "quantos orçamentos fiz em 10 min que antes levavam 40". Arredonde para meia hora.
- **Total de horas:** some as quatro colunas. Se quiser automatizar, use a fórmula `=SOMA(B3:E3)` na linha correspondente (a IA te ajuda: prompt 47 do Bônus 1).
- **Valor da sua hora (R$):** veja o cálculo abaixo. Preencha uma vez e repita nas semanas seguintes (revise a cada 6 meses).
- **Economia da semana (R$):** total de horas × valor da hora (`=F3*G3`).
- **Orçamentos enviados / Vendas fechadas:** copie da sua planilha de funil. São os números que mostram se a máquina de vendas está girando.
- **Observações:** o contexto que os números não contam ("feriado", "promoção rodando", "fiquei doente"). Sua memória de 3 meses atrás vai agradecer.

## Como calcular o valor da sua hora

Método simples e suficiente:

1. Quanto você quer/precisa tirar do negócio por mês? (ex: R$ 4.000)
2. Quantas horas você trabalha por mês? (ex: 50 h/semana × 4,3 = ~215 h)
3. Divida: R$ 4.000 ÷ 215 = **R$ 18,60/hora**.

Esse número costuma doer na primeira vez — e é exatamente por isso que ele importa: cada hora que os funcionários digitais devolvem é uma hora que você pode usar para produzir mais (aumentando o de cima) ou trabalhar menos (diminuindo o de baixo). Os dois movimentos aumentam o valor da sua hora.

## Como ler o resultado no fim do mês

No Relatório Mensal do Dono (capítulo 8), cole as 4 linhas do mês e observe três coisas:

1. **Economia acumulada do mês (R$):** o "salário" que os funcionários digitais pagaram. Compare com o custo deles (provavelmente R$ 0 a R$ 120). Esse é o seu ROI.
2. **Tendência do total de horas:** subindo nas primeiras semanas (você está pegando o jeito) e estabilizando depois é o padrão saudável. Caindo? Algum bloco da rotina está sendo pulado — descubra qual antes de culpar o sistema.
3. **Orçamentos × vendas:** se orçamentos sobem e vendas não, o problema é conversão (revise follow-up e preço). Se orçamentos caem, o problema é fluxo (acenda o Conteúdo).

Uma régua honesta para o primeiro trimestre: se a planilha mostrar **5+ horas/semana** economizadas de forma consistente, o sistema se pagou muitas vezes. Se mostrar menos de 2, volte ao capítulo 9 e verifique se os blocos da rotina estão de fato acontecendo — o sistema só economiza o tempo de quem o roda.
