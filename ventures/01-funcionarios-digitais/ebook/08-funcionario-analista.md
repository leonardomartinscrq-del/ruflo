# Capítulo 8 — Funcionário nº 5: O Analista de Mercado

Os quatro primeiros funcionários trabalham **dentro** do balcão: atendem, vendem, divulgam, organizam. O quinto trabalha de fora, olhando para o jogo inteiro — o que o concorrente está fazendo, se o seu preço está certo, o que os clientes dizem pelas costas (nas avaliações) e o que os números do mês significam.

Grande empresa paga caro por isso: chama-se consultoria. Você vai montar a sua por R$ 0 — com uma condição que eu preciso deixar clara já no primeiro parágrafo, porque é a regra número um deste capítulo:

**A IA não conhece a sua cidade.** Ela não sabe o preço do salão da esquina, nem quantos concorrentes abriram no seu bairro este ano. Se você perguntar, ela responde mesmo assim — inventando com a maior confiança do mundo (a alucinação do capítulo 1). Por isso, o Analista funciona num esquema fixo: **você coleta os dados, a IA organiza e analisa.** Você é o repórter; ela é a redação inteira. Nunca o contrário.

## O que esse funcionário faz

- **Pesquisa de concorrência estruturada:** transforma sua coleta de informações (preços, ofertas, presença digital dos concorrentes) numa análise comparativa com conclusões acionáveis.
- **Precificação:** analisa seus custos e posicionamento e sugere faixas de preço — com a decisão final sempre na sua mão.
- **Mineração de avaliações:** lê dezenas de reviews (suas e dos concorrentes) e extrai os padrões que ninguém tem paciência de tabular.
- **Teste de ofertas:** desenha variações de promoção e um jeito simples de medir qual funcionou.
- **Relatório mensal do dono:** pega os números da sua planilha (capítulo 7) e devolve um diagnóstico com 3 ações para o mês seguinte.

### O que ele NÃO faz

- **Não sabe fatos do mundo real por conta própria.** Preço de concorrente, demanda do bairro, salário médio da categoria: tudo que ela "souber" sem você fornecer é chute verossímil. Dados entram por você.
- **Não decide por você.** Ele recomenda com argumentos. Subir preço, abrir filial, cortar produto — decisões com consequência são do dono.
- **Não substitui sentir o cliente.** Análise organiza o que você já meio que sabia; a intuição de quem está no balcão todo dia continua sendo seu melhor sensor. O Analista existe para confirmá-la ou desafiá-la com dados.

## O que você precisa

| Ferramenta | Para quê | Custo |
|---|---|---|
| ChatGPT, Claude ou Gemini (grátis) | Toda a análise | Grátis |
| Manual do Funcionário (cap. 3) | Contexto do negócio | Pronto |
| Google Sheets (planilha do cap. 7) | Fonte dos seus números | Pronta |
| Google Maps, Instagram, iFood (os que valerem) | Coleta de dados de concorrência e avaliações | Grátis |
| 1h por mês | A rotina do Analista | — |

Custo total: **R$ 0**. Este funcionário trabalha 1 vez por mês — mas é a hora mais bem paga do seu mês.

## Montagem passo a passo

### Etapa 1 — O censo de concorrentes (30 min, 1x; atualiza a cada 3 meses)

Primeiro, a coleta. Escolha seus **5 concorrentes mais diretos** (mesmo serviço, mesma região ou mesmo público) e, para cada um, anote num bloco de notas:

- Nome e onde atende
- Preços que conseguir ver (site, cardápio, Instagram, perguntando como cliente — sim, pode)
- O que prometem (rapidez? luxo? preço baixo?)
- Presença digital: seguidores, frequência de post, responde comentário?
- Nota e quantidade de avaliações (Google Maps, iFood, etc.)
- Algo que fazem e você não (e vice-versa)

Não precisa ser perfeito; precisa ser real. Com a coleta em mãos, cole o Manual e:

```
Organize minha pesquisa de concorrência. Dados que eu coletei:

[COLAR SUAS ANOTAÇÕES DOS 5 CONCORRENTES]

Tarefa:
1. Monte uma tabela comparativa: eu + os 5 concorrentes, nas colunas
   preço, promessa principal, presença digital, avaliação, diferencial.
2. Aponte: onde estou mais caro/mais barato e se a diferença se
   justifica pelo que ofereço; o que 3 ou mais concorrentes fazem e
   eu não (pode ser padrão do mercado que o cliente já espera); e
   qual espaço NINGUÉM está ocupando.
3. Conclua com as 2 oportunidades mais práticas para mim nos
   próximos 30 dias.

Use SOMENTE os dados que forneci — onde faltar informação, escreva
"não coletado" em vez de estimar.
```

A última linha do prompt é a trava de segurança contra alucinação. Use-a em toda análise.

### Etapa 2 — A revisão de preços (40 min, a cada 6 meses ou quando o custo mudar)

Precificação no pequeno negócio costuma nascer assim: "cobrei mais ou menos o que o concorrente cobra". O Analista melhora isso em uma sessão. Antes, colete: seus custos diretos por produto/serviço (material, taxa de entrega, embalagem), suas horas envolvidas, e os preços de concorrência da Etapa 1.

```
Me ajude a revisar o preço de [PRODUTO/SERVIÇO].

Dados:
- Custos diretos por unidade: [LISTAR: material R$ X, embalagem R$ Y,
  taxa Z...]
- Meu tempo por unidade: [HORAS] (considere que quero que minha hora
  valha pelo menos R$ [VALOR — se não souber, me ajude a calcular
  perguntando minha meta de renda mensal e horas disponíveis])
- Preço atual: R$ [VALOR]
- Concorrentes: [FAIXAS DA ETAPA 1]
- Meu posicionamento: [mais barato / na média / premium — e por quê]

Tarefa:
1. Calcule meu custo real por unidade e minha margem atual (mostre a
   conta passo a passo).
2. Sugira 3 faixas de preço (defensiva, recomendada, ousada), cada
   uma com justificativa e risco.
3. Se a recomendada for acima da atual, sugira como comunicar o
   reajuste (sei que o capítulo 5 tem o prompt da mensagem).

A decisão final é minha: termine com as 3 perguntas que eu deveria
me fazer antes de bater o martelo.
```

O resultado mais comum dessa sessão, na vida real? Descobrir que a sua hora está valendo menos que o salário mínimo depois dos custos. Doloroso e libertador — porque agora é um número, não uma sensação, e número se corrige.

### Etapa 3 — Mineração de avaliações (30 min, 1x por trimestre)

Avaliações são pesquisa de mercado grátis que os clientes escreveram de graça — e quase nenhum dono lê de forma sistemática. Colete: todas as suas avaliações (Google Maps, iFood, comentários relevantes) e 20–30 dos seus 2 maiores concorrentes.

```
Analise estas avaliações de clientes.

MINHAS ([N] avaliações):
[COLAR]

CONCORRENTE A ([N] avaliações):
[COLAR]

CONCORRENTE B ([N] avaliações):
[COLAR]

Tarefa:
1. Padrões de ELOGIO meus: o que os clientes mais valorizam (isso é
   meu diferencial real — o que devo falar nos posts e na bio).
2. Padrões de RECLAMAÇÃO meus: agrupados por tema, com frequência.
3. Reclamações recorrentes DOS CONCORRENTES: cada uma é uma
   oportunidade minha (o que o mercado quer e não recebe).
4. Elogios recorrentes dos concorrentes que eu não recebo: o que
   eles fazem melhor (sem rodeio, preciso ouvir).
5. Conclua: 1 coisa para começar a fazer, 1 para corrigir, 1 para
   comunicar melhor.

Use somente o texto fornecido; se uma categoria tiver poucos dados,
diga isso em vez de extrapolar.
```

Dica de ouro escondida no item 1: **os elogios recorrentes são a sua copy pronta.** Se 8 clientes escreveram "entrega sempre no horário", a sua bio e seus posts de oferta deveriam gritar pontualidade — é o diferencial que o mercado já validou, com as palavras do próprio cliente.

### Etapa 4 — Teste de oferta com medição de pobre (que funciona) (30 min por rodada)

Promoção sem medição é palpite caro. O ciclo do Analista tem 3 passos:

**1. Gerar as variações:**

```
Quero testar uma oferta de [OBJETIVO: ex. aumentar movimento nas
terças / desovar estoque de X / atrair cliente novo].

Crie 3 variações de oferta com mecânicas DIFERENTES entre si (ex:
desconto direto vs. combo vs. brinde/upgrade vs. condição "traga um
amigo"), todas dentro destes limites: desconto máximo [X%], válidas
por [PERÍODO], sem comprometer [O QUE NÃO PODE: ex. margem do
carro-chefe, agenda de sábado].

Para cada uma: nome, mecânica, texto de divulgação de 3 linhas, e o
risco principal.
```

**2. Medir sem sistema caro** — dois truques de balcão:

- **Código no resgate:** cada variação tem uma palavra ("ME DIGA *TERÇA10*") — quem usa, você marca um risquinho. Conta exata, custo zero.
- **A pergunta de ouro:** todo cliente novo no período ouve "como você ficou sabendo?" — e a resposta vai para uma nota no celular.

**3. Fechar a rodada:** depois do período, volte à IA com os números ("variação A: 12 resgates, B: 3, C: 7; vendas totais...") e peça o veredito + a próxima rodada. Promoção vira experimento, e experimento acumula aprendizado.

### Etapa 5 — O Relatório Mensal do Dono (30 min, todo início de mês)

A joia da coroa — e o prompt mais importante do capítulo. Todo dia 1º, pegue da planilha do capítulo 7: faturamento do mês, gastos por categoria, e da planilha de funil (capítulo 5): orçamentos enviados/fechados. Aí:

```
Você é meu analista de negócio. Aqui estão meus números de [MÊS]:

- Faturamento: R$ [X] (mês anterior: R$ [Y])
- Gastos por categoria: [COLAR DA PLANILHA]
- Orçamentos enviados: [N] | Fechados: [N] | Taxa: [%]
- Ticket médio: R$ [X]
- Observações do mês: [o que aconteceu de atípico: feriado, você
  doente, promoção rodando, equipamento quebrado...]

Tarefa:
1. Diagnóstico em até 10 linhas: o que melhorou, o que piorou e a
   provável causa (considere as observações antes de concluir
   tendência).
2. O número mais preocupante e o mais animador do mês.
3. EXATAMENTE 3 ações para o próximo mês, em ordem de impacto, cada
   uma com: o que fazer, qual funcionário digital deste livro ajuda
   nisso, e como saber se funcionou no fim do mês.

Seja direto. Se os dados não sustentam uma conclusão, diga "não dá
para afirmar com um mês de dado" em vez de inventar tendência.
```

Nos primeiros meses, o relatório será simples — pouca série histórica. Do terceiro mês em diante, quando a IA puder comparar tendências, ele vira a reunião de diretoria que o seu negócio nunca teve. Guarde cada relatório no mesmo Google Doc, em ordem: esse histórico é um ativo.

## Prompts prontos

Seis situações recorrentes do Analista (Manual colado antes):

**1. Concorrente novo abriu na região** — *quando usar: na semana em que você descobrir.*

```
Abriu um concorrente novo: [O QUE VOCÊ SABE: nome, proposta, preços
vistos, promoção de inauguração]. Sem alarmismo: o que ele ameaça de
verdade no meu negócio, o que é só barulho de inauguração, e quais 2
movimentos defensivos fazem sentido AGORA (sem guerra de preço)?
Use só o que informei; liste o que mais eu deveria descobrir sobre ele.
```

**2. Devo adicionar este produto/serviço?** — *quando usar: antes de expandir o cardápio/portfólio.*

```
Estou pensando em oferecer [NOVO PRODUTO/SERVIÇO]. Contexto: [por que
estou considerando: clientes pedem? concorrente tem? margem boa?].
Monte uma análise prós/contras específica do meu negócio: encaixe com
meu cliente atual, impacto na operação (tempo/equipamento), faixa de
preço coerente com meu posicionamento, e os 3 riscos principais.
Termine com as perguntas que eu deveria responder antes de decidir
— inclusive como testar pequeno antes de comprometer.
```

**3. Tradutor de sazonalidade** — *quando usar: planejando o trimestre.*

```
Para meu tipo de negócio, monte o mapa de sazonalidade dos próximos 3
meses no Brasil: datas comemorativas relevantes, períodos
historicamente fortes e fracos PARA O MEU SETOR (se não tiver certeza
sobre meu setor específico, diga e pergunte), e 1 ação de preparação
para cada momento-chave, com antecedência sugerida.
```

**4. Autópsia de mês ruim** — *quando usar: quando o faturamento despencar e o pânico bater.*

```
Meu faturamento caiu [X%] em [MÊS]. Fatos: [TUDO QUE SOUBER: chuva,
obra na rua, concorrente em promoção, você postou menos, feriados,
economia local...]. Liste as hipóteses de causa em ordem de
probabilidade, separando o que estava sob meu controle do que não
estava, e me diga que dado coletar para confirmar cada hipótese
antes de eu sair mudando tudo.
```

**5. Pesquisa rápida com clientes (feita certa)** — *quando usar: 2x por ano, ou antes de mudança grande.*

```
Quero ouvir meus clientes sobre [TEMA: novo horário? novo produto?
por que compram aqui?]. Crie uma mini-pesquisa de NO MÁXIMO 4
perguntas para WhatsApp: 3 fechadas (fáceis de responder com um
toque) e 1 aberta. Inclua a mensagem-convite (curta, explicando que
leva 1 minuto e como o cliente se beneficia) e me diga como tabular
as respostas numa planilha simples.
```

**6. Comparador de fornecedores** — *quando usar: cotação de insumo ou serviço relevante.*

```
Cotei [INSUMO/SERVIÇO] com 3 fornecedores: [COLAR: preço, prazo,
mínimo, frete, observações de cada]. Monte a comparação incluindo o
custo TOTAL real de cada um (não só o preço de tabela), aponte
pegadinhas comuns nesse tipo de contratação que eu deveria conferir,
e recomende com justificativa. Decisão final é minha.
```

## Teste de qualidade

- [ ] Rode a pesquisa de concorrência e procure na resposta algum "fato" que você **não** forneceu. Achou? A IA extrapolou — reforce a trava ("use somente os dados que forneci") e refaça.
- [ ] Na revisão de preço, refaça a conta de custo no papel ou na calculadora. A IA erra aritmética com confiança; a estrutura da análise vale mais que a conta — a conta é sua.
- [ ] No relatório mensal, confira se as 3 ações são executáveis por você em um mês. "Melhore seu marketing" não é ação; "publique os 12 posts do calendário e meça quantos 'vim pelo Instagram' aparecem" é.
- [ ] Releia uma análise 24h depois, com cabeça fria. Continua fazendo sentido ou você se empolgou junto com a IA?

## Erros comuns

1. **Perguntar à IA o que ela não tem como saber.** "Quanto cobra o salão X do bairro Y?" — ela responde, e é chute. Tudo que é fato local entra coletado por você. Sem exceção.
2. **Terceirizar a decisão.** "A IA mandou subir o preço" não existe. Ela monta o caso; quem assina é você — inclusive porque é você quem conhece o cliente que vai reagir.
3. **Análise sem dado mínimo.** Relatório mensal com "faturamento: uns 5 mil, acho" devolve análise no mesmo nível. O Analista é o motivo de manter a planilha do capítulo 7 em dia — eles trabalham em dupla.
4. **Coletar uma vez e usar para sempre.** Pesquisa de concorrência de 8 meses atrás descreve um mercado que não existe mais. Censo a cada 3 meses, preço a cada 6.
5. **Mudar três coisas ao mesmo tempo depois de uma análise.** Se você muda preço, oferta e horário na mesma semana, nunca saberá o que causou o quê. Uma mudança por vez, medida pelo truque do código de resgate.
6. **Ignorar a conclusão que doeu.** A mineração de avaliações às vezes devolve "os clientes do concorrente elogiam a rapidez; os seus reclamam da demora". Análise que só confirma o que você queria ouvir é horóscopo.

## Quanto tempo isso economiza

Aqui a régua certa não é tempo economizado — é **acesso ao que você não tinha**. Uma consultoria júnior cobraria algumas centenas de reais por uma análise de concorrência ou revisão de precificação; o Analista faz versões úteis disso por zero, em 1h por mês.

Mas dá para fazer uma conta honesta de tempo também: tabular 60 avaliações à mão (ler, agrupar, contar temas) leva facilmente 3–4 horas — a IA faz a tabulação em 1 minuto e você gasta 20 revisando. Montar uma comparação de concorrência apresentável: uma tarde inteira no Excel vs. 40 minutos no esquema coleta-sua + análise-dela. Por mês, a rotina completa do Analista (relatório mensal + 1 análise pontual) custa **~1h e devolve o que antes simplesmente não era feito** — e decisão melhor não aparece na planilha de horas, aparece na de faturamento.

Cinco funcionários contratados. Falta o mais importante: fazer todos trabalharem juntos sem virar mais uma fonte de caos na sua semana. É o assunto do próximo capítulo.
