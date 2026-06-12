# Capítulo 7 — Funcionário nº 4: O Assistente Administrativo e Financeiro

Tem uma cena que se repete em quase todo pequeno negócio do Brasil, e ela não acontece no balcão. Acontece à noite, em casa.

É a marceneira de Curitiba que precisa mandar um orçamento desde anteontem, mas trava na hora de montar o documento. É o personal trainer de Salvador que tem três alunos com mensalidade atrasada e não cobra porque "fica chato". É a dona da loja de roupas infantis em Goiânia que jurou que esse mês ia anotar tudo que entra e sai — e já é dia 19.

O trabalho administrativo é o que menos aparece e o que mais pesa. Ninguém abre um negócio porque ama emitir recibo. E é exatamente por isso que ele é o serviço perfeito para o seu quarto funcionário digital: é repetitivo, é baseado em texto e segue padrões. O tipo de tarefa em que a IA é melhor — desde que você confira o resultado, como sempre.

Neste capítulo, você vai montar o assistente que cuida de orçamentos, cobranças, controle financeiro básico, agenda e documentos simples. Como nos capítulos anteriores, tudo parte do seu Manual do Funcionário (aquele documento-mestre do Capítulo 3): cole o Manual no início da conversa, e só depois use os prompts daqui.

## O que esse funcionário faz (e o que NÃO faz)

**O que ele faz bem:**

- **Orçamentos padronizados.** Você dá os dados (serviço, quantidade, prazo, preço), ele devolve um orçamento formatado, profissional, no seu padrão, em minutos.
- **Mensagens de cobrança em três níveis.** Do lembrete amistoso ao aviso formal, com o tom certo em cada etapa — sem você ter que escolher cada palavra com medo de ofender.
- **Estrutura de controle financeiro no Google Sheets.** Ele desenha a planilha de entradas e saídas, escreve as fórmulas e explica o que cada uma faz. Você só cola.
- **Mensagens de agenda.** Confirmação de horário, lembrete de véspera, reagendamento educado. É a arma mais barata que existe contra o no-show (cliente que marca e não aparece).
- **Minutas de documentos simples.** Rascunho de recibo, rascunho de termo de serviço. Atenção à palavra *rascunho* — daqui a pouco eu explico o limite disso, e ele é sério.

**O que ele NÃO faz:**

- **Não substitui contador.** Imposto, MEI, nota fiscal, pró-labore, regime tributário: isso é trabalho de contador, e errar aí custa caro. A IA pode te ajudar a *entender* um termo que o contador usou, mas não pode assumir a função dele.
- **Não substitui advogado.** Minuta de IA é rascunho. Contrato que protege você de verdade precisa passar por um profissional. Vou repetir isso com todas as letras na seção de montagem.
- **Não acessa sua conta bancária nem paga boleto.** Ele organiza, redige e calcula em cima do que você informa. Quem digita os números e aperta os botões do banco é você.
- **Não sabe quem já pagou.** Se você mandar a IA gerar uma cobrança para alguém que pagou ontem, ela gera — caprichada e tudo. Conferir o pagamento antes de cobrar é trabalho seu, sempre.
- **Não decide preço, prazo nem desconto.** Ele formata a decisão que você já tomou.

## O que você precisa

A lista é curta:

1. **Seu Manual do Funcionário** (Capítulo 3) atualizado, com: nome do negócio, CNPJ ou CPF profissional se tiver, lista de serviços/produtos com preços, formas de pagamento aceitas, chave Pix, política de prazo e de sinal (se houver).
2. **Uma conta no ChatGPT, Claude ou Gemini** — a mesma que você já usa desde o Capítulo 2. Plano gratuito serve para começar.
3. **Google Sheets** (gratuito, no celular ou computador) para o controle financeiro.
4. **WhatsApp Business** para enviar orçamentos, cobranças e confirmações.
5. **Trinta minutos de dados reunidos:** seus últimos 3 orçamentos enviados (do jeito que saíram, mesmo que feios), e a lista de quem está te devendo hoje, com valor e data de vencimento.
6. **Cerca de 2 horas para a montagem inicial**, de preferência divididas em dois dias para não cansar.

## Montagem passo a passo

### Passo 1 — Crie seu template de orçamento (30 min)

Um orçamento padronizado faz duas coisas: passa profissionalismo e evita esquecimento (validade, prazo, forma de pagamento — itens que, quando faltam, viram dor de cabeça depois).

Abra uma conversa nova com sua IA, cole o Manual do Funcionário e use o **Prompt 1** da seção de prompts. A IA vai te devolver um modelo com campos fixos. Revise: tire o que não faz sentido para o seu tipo de negócio, ajuste o tom. Salve esse template num lugar fácil (uma nota no celular, um doc no Drive). Ele vira parte do seu Manual.

A partir daí, gerar um orçamento novo é só usar o **Prompt 2**: você informa os dados do pedido, a IA preenche o template. Você confere os números — *sempre* os números — e envia.

### Passo 2 — Monte sua régua de cobrança em 3 níveis (30 min)

"Régua de cobrança" é só um nome bonito para uma sequência combinada de mensagens. A sua terá três níveis:

| Nível | Quando | Tom |
|-------|--------|-----|
| 1 — Lembrete amistoso | 1 dia após o vencimento (D+1) | Leve, dá o benefício da dúvida ("pode ter passado batido") |
| 2 — Cobrança firme | 7 dias após o vencimento (D+7) | Educado, mas direto: cita valor, data e pede retorno |
| 3 — Aviso formal | 15 dias após o vencimento (D+15) | Sério, menciona consequência real (pausa do serviço, por exemplo) |

Use os **Prompts 3, 4 e 5** para gerar os três modelos de uma vez, já no seu tom de voz. Guarde os três prontos. Quando alguém atrasar, você só troca o nome, o valor e a data — 2 minutos, sem o desgaste emocional de redigir do zero.

Duas regras de ouro aqui:

- **Antes de enviar qualquer cobrança, confira se o pagamento realmente não caiu.** Cobrar quem já pagou queima a relação mais rápido do que o atraso queimaria.
- **Consequência anunciada no nível 3 tem que ser real e proporcional.** Não escreva "medidas judiciais" por um corte de cabelo de R$ 60. Se for pausar o serviço, diga que vai pausar o serviço.

### Passo 3 — Crie seu controle financeiro no Google Sheets (40 min)

Aqui está o pulo do gato deste capítulo: você não precisa saber fórmula de planilha. **A IA escreve a fórmula, explica o que ela faz, e você cola.**

1. Crie uma planilha nova no Google Sheets, chamada "Financeiro [SEU NEGÓCIO] 2026".
2. Cole o Manual na IA e use o **Prompt 6**. Ele pede a estrutura completa: aba de entradas, aba de saídas, categorias adequadas ao seu ramo e as fórmulas de soma por categoria e saldo do mês.
3. A IA vai responder com algo assim: "Na célula B2 da aba Resumo, cole: `=SOMASE(Saídas!C:C;"Insumos";Saídas!B:B)` — esta fórmula soma tudo que você marcou como Insumos na aba de Saídas."
4. Cole as fórmulas exatamente onde a IA indicar. Se aparecer erro (acontece, principalmente por causa de ponto-e-vírgula ou nome de aba diferente), copie a mensagem de erro e cole de volta na conversa: "deu este erro, corrija". A IA corrige.
5. **Teste com dados fictícios antes de usar de verdade.** Lance três entradas e três saídas inventadas, some na calculadora do celular e confira se a planilha bate. Só depois apague os testes e comece a usar.

O hábito que sustenta tudo: lançar entradas e saídas **uma vez por semana** (não diariamente — combinaremos isso na rotina do Passo 6). Planilha perfeita abandonada vale menos que planilha simples alimentada.

### Passo 4 — Mensagens de agenda e antídoto contra no-show (20 min)

Se o seu negócio trabalha com horário marcado — salão, consultório, estúdio de tatuagem, aula particular, assistência técnica com visita — o no-show é dinheiro evaporando. A defesa é simples e comprovada na prática de qualquer recepção bem treinada: **confirmação na marcação + lembrete na véspera**.

Use o **Prompt 7** para gerar seu kit de mensagens de agenda: confirmação de horário marcado, lembrete de véspera pedindo um "confirmado?", e mensagem de reagendamento sem clima ruim. Salve as três como respostas rápidas no WhatsApp Business (você aprendeu a fazer isso no Capítulo 4, com o Atendente).

Não elimina o no-show — nada elimina — mas reduzir de, digamos, quatro faltas por semana para uma ou duas já paga o capítulo inteiro.

### Passo 5 — Minutas de documentos simples (20 min)

A IA rascunha bem dois documentos que todo pequeno negócio precisa:

- **Recibo de pagamento** — simples, de baixo risco, e o **Prompt 8** resolve.
- **Termo simples de prestação de serviço** — uma página descrevendo o que será feito, valor, prazo, o que está incluído e o que não está.

E aqui vem o aviso, sem suavizar:

> **⚠️ AVISO IMPORTANTE — leia duas vezes.**
> Minuta gerada por IA **não substitui advogado**. A IA não conhece a lei brasileira em profundidade, não conhece as particularidades do seu caso e pode escrever cláusulas inválidas ou que te prejudicam — com a maior confiança do mundo. Use a minuta como **rascunho para baratear e acelerar a revisão profissional**: chegar para um advogado com um rascunho organizado custa menos do que pedir um contrato do zero. Para serviços de valor alto, contratos com obrigações de longo prazo, locação, sociedade ou qualquer coisa que envolva risco real, a revisão por advogado não é opcional. É a diferença entre economizar algumas centenas de reais hoje e perder alguns milhares depois.

Para o termo simples do dia a dia (o combinado de um serviço de R$ 200, por exemplo), o rascunho da IA revisado por você já organiza a relação e evita o famoso "mas você não falou que...". Para tudo acima disso: advogado.

### Passo 6 — A rotina administrativa de 40 minutos (fixe no calendário)

Tudo que você montou acima só funciona com uma rotina. A boa notícia: ela cabe em **40 minutos, uma vez por semana**. Sugestão: sexta-feira no fim do expediente, ou o dia que for mais calmo no seu ramo.

| Bloco | Tempo | O que fazer |
|-------|-------|-------------|
| 1. Lançamentos | 15 min | Lançar entradas e saídas da semana na planilha (extrato do banco aberto do lado) |
| 2. Cobranças | 10 min | Olhar quem venceu, conferir quem pagou, disparar nível 1, 2 ou 3 conforme o caso |
| 3. Orçamentos pendentes | 10 min | Algum orçamento prometido e não enviado? Gera e envia agora |
| 4. Agenda da semana seguinte | 5 min | Conferir horários marcados e programar confirmações |

Quarenta minutos. Coloque alarme recorrente no celular com o nome "Reunião com meu assistente administrativo". Parece bobagem, mas nomear ajuda a não pular.

## Prompts prontos

Lembrete que vale para todos: **cole primeiro o seu Manual do Funcionário na conversa**, depois o prompt. E nunca envie com os [COLCHETES] sem preencher.

**Prompt 1 — Criar o template de orçamento**
*Quando usar: uma vez só, na montagem. Depois, é só reutilizar o template.*

```
Com base no Manual do Funcionário acima, crie um modelo de orçamento
profissional para eu enviar por WhatsApp e por PDF.

O modelo deve ter os campos:
- Cabeçalho com [NOME DO NEGÓCIO] e contato
- Nome do cliente e data
- Descrição do serviço/produto em itens, com quantidade e valor unitário
- Valor total em destaque
- Prazo de execução/entrega
- Formas de pagamento: [SUAS FORMAS DE PAGAMENTO]
- Validade do orçamento: [X DIAS]
- Observações (o que está incluso e o que NÃO está incluso)

Tom: profissional e simpático, sem formalidade exagerada.
Me entregue em duas versões: uma curta para mensagem de WhatsApp
e uma completa para documento.
```

**Prompt 2 — Preencher um orçamento novo**
*Quando usar: toda vez que um cliente pedir orçamento.*

```
Use o template de orçamento que criamos. Preencha com estes dados:

- Cliente: [NOME DO CLIENTE]
- Serviço/produto: [DESCRIÇÃO DO QUE O CLIENTE PEDIU]
- Quantidade: [QUANTIDADE]
- Valor: [VALOR QUE VOCÊ DEFINIU — a IA não inventa preço]
- Prazo: [PRAZO QUE VOCÊ CONSEGUE CUMPRIR]
- Observações: [INCLUSOS E NÃO INCLUSOS DESTE CASO]

Gere a versão WhatsApp e a versão completa. Não altere nenhum valor
e não acrescente serviços que eu não listei.
```

**Prompt 3 — Cobrança nível 1: lembrete amistoso (D+1)**
*Quando usar: 1 dia após o vencimento, depois de conferir que o pagamento não caiu.*

```
Escreva uma mensagem curta de WhatsApp lembrando um cliente de um
pagamento que venceu ontem. Contexto:

- Cliente: [NOME]
- Serviço: [SERVIÇO PRESTADO]
- Valor: [VALOR]
- Venceu em: [DATA]
- Chave Pix: [SUA CHAVE PIX]

Tom: leve e amistoso, assumindo que provavelmente foi esquecimento.
Sem tom de cobrança pesada. No máximo 4 frases. Termine se colocando
à disposição para qualquer dúvida.
```

**Prompt 4 — Cobrança nível 2: firme e educada (D+7)**
*Quando usar: 7 dias após o vencimento, se o nível 1 não resolveu.*

```
Escreva uma mensagem de cobrança para um pagamento atrasado há 7 dias.
Já enviei um lembrete leve e não tive retorno. Contexto:

- Cliente: [NOME]
- Serviço: [SERVIÇO PRESTADO]
- Valor: [VALOR]
- Venceu em: [DATA]
- Chave Pix: [SUA CHAVE PIX]

Tom: educado, mas firme e direto. Cite o valor e a data de vencimento.
Pergunte se houve algum problema e peça uma previsão de pagamento.
Ofereça [SUA ALTERNATIVA, ex.: parcelamento ou nova data] se fizer
sentido. No máximo 6 frases.
```

**Prompt 5 — Cobrança nível 3: aviso formal (D+15)**
*Quando usar: 15 dias após o vencimento, antes de qualquer providência concreta.*

```
Escreva uma mensagem formal de cobrança para um pagamento atrasado
há 15 dias, após dois contatos sem solução. Contexto:

- Cliente: [NOME]
- Serviço: [SERVIÇO PRESTADO]
- Valor: [VALOR]
- Venceu em: [DATA]
- Consequência real se não houver retorno até [DATA-LIMITE]:
  [EX.: suspensão do serviço / não agendamento de novos trabalhos]

Tom: formal, respeitoso e objetivo. Sem ameaças vazias e sem
mencionar medidas que eu não citei. Deixe claro que prefiro
resolver por acordo e indique um prazo final para contato.
```

**Prompt 6 — Estrutura da planilha financeira + fórmulas**
*Quando usar: uma vez, na montagem do controle financeiro.*

```
Quero montar um controle financeiro simples no Google Sheets para o
meu negócio: [TIPO DE NEGÓCIO, ex.: marmitaria com entrega].
Não entendo de fórmulas, então me guie célula por célula.

Crie:
1. Aba "Entradas": data, descrição, categoria, forma de pagamento, valor
2. Aba "Saídas": data, descrição, categoria, valor
3. Sugira de 5 a 8 categorias de saída adequadas ao meu ramo
4. Aba "Resumo do Mês" com: total de entradas, total de saídas,
   saldo, e total por categoria

Para cada fórmula: diga em QUAL célula colar, escreva a fórmula
pronta para o Google Sheets em português (com ponto-e-vírgula),
e explique em uma frase o que ela faz.
```

**Prompt 7 — Kit de mensagens de agenda (anti no-show)**
*Quando usar: uma vez, para criar os modelos; depois é só usar as respostas rápidas.*

```
Crie 3 mensagens de WhatsApp para a agenda do meu negócio
[TIPO DE NEGÓCIO]:

1. CONFIRMAÇÃO DE AGENDAMENTO: enviada na hora em que o cliente
   marca. Deve repetir dia, horário e [ENDEREÇO OU LINK], e citar
   minha política de cancelamento: [SUA POLÍTICA, ex.: avisar com
   24h de antecedência].
2. LEMBRETE DE VÉSPERA: enviada um dia antes, pedindo uma
   confirmação simples (responder "confirmado").
3. REAGENDAMENTO SEM CLIMA RUIM: para quando o cliente desmarca,
   mantendo a porta aberta e já oferecendo dois novos horários:
   [OPÇÃO 1] e [OPÇÃO 2].

Tom: [SEU TOM, ex.: simpático e informal, com no máximo 1 emoji].
Use [NOME] como espaço para o nome do cliente.
```

**Prompt 8 — Minuta de recibo e termo simples de serviço**
*Quando usar: para gerar os rascunhos-base; revise sempre, e leve ao advogado o que tiver valor ou risco relevante.*

```
Preciso de dois rascunhos de documentos simples para o meu negócio
[TIPO DE NEGÓCIO]. Sei que isso é apenas uma minuta e que vou revisar
com um profissional o que for além do básico.

1. RECIBO DE PAGAMENTO com campos: nome e CPF/CNPJ de quem paga,
   valor por extenso e em números, referente a quê, data, cidade
   [SUA CIDADE] e assinatura.

2. TERMO SIMPLES DE PRESTAÇÃO DE SERVIÇO (1 página, linguagem
   clara) com: partes, descrição do serviço [SERVIÇO], valor e
   forma de pagamento, prazo, o que está incluído, o que NÃO está
   incluído, e política de cancelamento [SUA POLÍTICA].

Não invente cláusulas sobre multas ou juros — deixe o campo
indicado como [A DEFINIR] para eu decidir com orientação adequada.
```

## Teste de qualidade

Antes de considerar o funcionário "contratado", rode esta bateria de testes. Quinze minutos, papel e caneta (ou bloco de notas):

1. **Teste do orçamento com pegadinha.** Gere um orçamento pelo Prompt 2, mas confira número por número: valor unitário, total, prazo. A IA errou ou "completou" algo que você não pediu? Se sim, ajuste o prompt acrescentando "não inclua nada que eu não informei" e teste de novo.
2. **Teste da planilha com dados fictícios.** Três entradas e três saídas inventadas, soma na calculadora, comparação com o Resumo. Tem que bater centavo por centavo. Se não bater, cole o erro na IA e peça correção.
3. **Teste da cobrança lida em voz alta.** Leia os três níveis em voz alta, imaginando que você é o cliente. O nível 1 parece leve mesmo? O nível 3 parece sério sem ser ofensivo? Se algo soar como você jamais falaria, peça para a IA reescrever "mais parecido com este exemplo meu" e cole uma mensagem sua real.
4. **Teste do recibo.** Gere um recibo com dados fictícios e confira se todos os campos obrigatórios estão lá (valor por extenso é o que a IA mais esquece).
5. **Teste de envio real supervisionado.** Na primeira semana, use tudo em casos reais, mas com atenção redobrada. Depois de 5 a 10 usos sem sustos, você confia no fluxo — nunca a ponto de parar de revisar números.

## Erros comuns

**1. Deixar a IA "estimar" valores.** Se você não informa o preço, a IA inventa um — plausível, formatado e errado. Todo prompt de orçamento deste capítulo exige que *você* informe o valor. Mantenha assim.

**2. Cobrar sem conferir o extrato.** O cliente pagou ontem à noite, você cobra hoje cedo. Resultado: constrangimento e cliente com razão para reclamar. Conferência de pagamento vem antes de qualquer mensagem de cobrança, sempre.

**3. Confiar na fórmula sem testar.** Fórmula de planilha errada é pior que planilha nenhuma, porque te dá um número falso com cara de verdade. O teste com dados fictícios do Passo 3 não é opcional.

**4. Tratar a minuta como contrato pronto.** Imprimir o termo gerado pela IA, assinar com cliente em serviço de R$ 15 mil e descobrir depois que uma cláusula não vale nada. Minuta é rascunho. Valor alto ou risco real = advogado. Sem exceção.

**5. Colar dados sensíveis do cliente na IA.** CPF, dados de cartão, informações de saúde: nada disso entra em ferramenta de IA. Use "[NOME]", "[CPF]" e preencha depois, fora da ferramenta. O Capítulo 10 trata disso a fundo, mas a regra começa a valer agora.

**6. Abandonar a planilha na terceira semana.** O erro não é técnico, é de rotina. Quem tenta lançar todo dia desiste; quem lança uma vez por semana, com alarme marcado, continua. Se você pulou uma semana, não tente reconstituir tudo: lance o que conseguir pelo extrato e siga em frente. Planilha 85% completa e viva vale mais que planilha perfeita e morta.

**7. Mandar os três níveis de cobrança de uma vez.** A régua funciona porque dá tempo e escala o tom aos poucos. Pular direto para o nível 3 com dois dias de atraso queima relacionamento por nada.

## Quanto tempo isso economiza

A conta honesta, sem inflar:

| Tarefa | Sem assistente | Com assistente | Frequência típica |
|--------|----------------|----------------|--------------------|
| Montar e enviar orçamento | 20–40 min (e muitas vezes nem sai) | 5–10 min | 2–8 por semana |
| Redigir cobrança | 15 min + dias de adiamento | 2–3 min | 2–6 por mês |
| Controle financeiro | Não existia, ou 2h de sofrimento no fim do mês | 15 min por semana | semanal |
| Confirmações de agenda | 5–10 min improvisando | 1 min com resposta rápida | diária, se trabalha com horário |
| Recibo/termo simples | 30 min ou "depois eu faço" | 5 min + revisão | eventual |

Somando para um negócio típico: algo entre **2 e 4 horas por semana**, *depois* das 2 horas de montagem inicial e do primeiro mês de ajustes. Se na sua realidade der 1 hora e meia, ainda é um turno inteiro recuperado por mês.

Mas a verdade é que o maior ganho deste funcionário não é tempo — é **dinheiro que deixava de entrar**. Cobrança adiada é, na prática, desconto involuntário. Orçamento que demora três dias é venda que esfria. Horário vago por no-show é custo fixo sem receita. O assistente administrativo não vende nada; ele só fecha as torneiras por onde o seu dinheiro vazava em silêncio.

E tem um efeito que não cabe em tabela: a sensação de ter o financeiro sob controle. Quem nunca passou um dia 19 sem saber se o mês está no azul não sabe o peso que isso tira das costas.

No próximo capítulo, você contrata o quinto e último funcionário — o Analista de Mercado, que pega justamente os números desta planilha e transforma em decisões.
