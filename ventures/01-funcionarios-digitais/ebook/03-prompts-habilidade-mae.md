# Capítulo 3 — A habilidade-mãe: prompts que funcionam

Se este livro fosse um curso de culinária, este capítulo seria o de afiar facas. Parece menos empolgante que a receita do prato principal, mas é o que separa quem cozinha bem de quem se machuca.

Aqui está a verdade que ninguém te conta: **a diferença entre quem acha IA "genérica e inútil" e quem economiza 10 horas por semana não é a ferramenta. É a pergunta.** As duas pessoas usam o mesmo ChatGPT grátis. Uma escreve "faz um post pro meu negócio" e recebe um texto que serve para qualquer loja do planeta. A outra escreve uma instrução de 8 linhas e recebe um post que parece ter saído da cabeça dela num dia inspirado.

Este capítulo te ensina a segunda forma. E te entrega o documento mais importante do livro inteiro: o **Manual do Funcionário**, que você vai usar em todos os capítulos daqui para frente.

## Por que 90% das pessoas usa IA do jeito errado

A IA não lê mentes. Ela responde exatamente à pergunta que recebeu — e preenche tudo o que você não disse com o "média de tudo": o tom médio, o negócio médio, o cliente médio. Por isso a resposta sai genérica: porque a pergunta foi genérica.

Veja a diferença na prática:

**Prompt vago:**

```
Escreve uma mensagem de cobrança pra um cliente.
```

O que sai: uma mensagem formal, fria, em português de banco, começando com "Prezado cliente, vimos por meio desta...". Tecnicamente correta. Inútil para o seu negócio.

**Prompt completo:**

```
Você é assistente de comunicação de um estúdio de pilates de bairro,
tom acolhedor e direto, sem formalidade de banco.

A cliente [NOME] está com a mensalidade de [MÊS] atrasada há 5 dias.
Ela é aluna há 2 anos, nunca atrasou antes. Quero lembrar sem
constranger — provavelmente só esqueceu.

Escreva uma mensagem de WhatsApp de até 4 linhas, leve, que lembre do
pagamento e já ofereça a chave Pix. Sem a palavra "inadimplente",
sem tom de aviso. Termine com algo pessoal sobre a aula.
```

O que sai: uma mensagem que você enviaria sem mudar quase nada. A diferença não foi a IA. Foi a instrução.

A boa notícia: instrução boa tem fórmula. E a fórmula cabe numa sigla.

## A estrutura P-C-T-F-E

Todo prompt que funciona bem tem até cinco ingredientes. Você não precisa usar os cinco sempre — mas precisa saber quais existem para escolher.

| Letra | Ingrediente | O que é | Exemplo |
|---|---|---|---|
| **P** | **Papel** | Quem a IA deve ser | "Você é uma vendedora experiente de loja de roupas femininas" |
| **C** | **Contexto** | A situação e os fatos | "Cliente perguntou o preço, eu respondi, ela sumiu há 3 dias" |
| **T** | **Tarefa** | O que você quer, em verbo | "Escreva uma mensagem de follow-up" |
| **F** | **Formato** | Como a resposta deve vir | "Até 3 linhas, tom leve, com 1 pergunta no final" |
| **E** | **Exemplo** | Uma amostra do que você gosta | "Parecida com esta que funcionou: [colar]" |

Memorize assim: **Papel, Contexto, Tarefa, Formato, Exemplo**. Quando uma resposta da IA vier ruim, volte nessa lista e pergunte: qual ingrediente eu esqueci? Em 9 de 10 casos, foi o Contexto.

### Os dois ingredientes que mais mudam o resultado

**Contexto** é o rei. A IA não sabe o que você vende, quanto custa, nem como seus clientes falam. Tudo o que ela não souber, ela inventa ou genericiza. Regra prática: se um funcionário novo, no primeiro dia, precisaria daquela informação para fazer a tarefa, a IA também precisa.

**Formato** é o que poupa retrabalho. Sem formato, a IA adora entregar três parágrafos pomposos quando você queria duas linhas de WhatsApp. Diga o tamanho, o canal, o tom e o que não pode ter ("sem emoji", "sem 'imperdível'", "sem caps lock").

## Antes e depois: três casos reais

### Caso 1 — A doceira e o post de encomenda

**Antes:** `"Faz um post sobre bolo de pote"` → texto genérico com "delícia irresistível" e hashtag #bolodepote. Podia ser de qualquer doceria do Brasil.

**Depois:**

```
Você é social media de uma doceria artesanal de bairro que vende por
encomenda no WhatsApp (não tem loja física).

Contexto: semana que vem é dia dos namorados. Meu carro-chefe é o bolo
de pote de ninho com morango (R$ 14). Minhas clientes são mulheres de
25-45 anos do bairro, que compram para presentear ou para o "momento
café da tarde". Encomendas fecham quarta-feira.

Tarefa: escreva 1 legenda de post para Instagram anunciando o kit de
dia dos namorados (2 bolos de pote + cartãozinho, R$ 30).

Formato: gancho na primeira linha (sem "atenção!"), corpo de até 5
linhas, preço claro, chamada para "pedir no link da bio", 3 hashtags
locais no máximo. Tom carinhoso, sem ser meloso.
```

**O que mudou:** a IA agora sabe o produto, o preço, o prazo, a cliente e a ocasião. A legenda sai pronta para publicar.

### Caso 2 — O eletricista e o orçamento

**Antes:** `"Escreve um orçamento de serviço elétrico"` → um documento de empresa grande, com "proposta comercial nº 001/2026" e termos que assustam cliente residencial.

**Depois:**

```
Você é assistente administrativo de um eletricista autônomo que atende
residências.

Contexto: visitei o apartamento da cliente [NOME] hoje. Serviço:
trocar o chuveiro (cliente compra o aparelho), instalar 4 tomadas na
cozinha e revisar o disjuntor que desarma. Materiais por minha conta:
[LISTAR]. Mão de obra: R$ [VALOR]. Prazo: 1 dia. Garantia do serviço:
90 dias. Pagamento: Pix ou cartão (com acréscimo da maquininha).

Tarefa: monte o orçamento em formato de mensagem de WhatsApp.

Formato: saudação curta, lista do que está incluído, valor total
destacado, validade de 7 dias, forma de pagamento, e fechamento
perguntando se posso agendar. Linguagem simples, profissional, sem
"prezado".
```

**O que mudou:** virou um orçamento que cabe no WhatsApp — onde o cliente dele realmente decide.

### Caso 3 — A nutricionista e a pergunta de preço

**Antes:** `"Como responder quando perguntam o preço da consulta?"` → resposta de blog, com 5 estratégias teóricas e nenhuma mensagem pronta.

**Depois:**

```
Você é secretária de uma nutricionista que atende online e presencial.

Contexto: recebi no Direct a mensagem "oi, quanto é a consulta?".
Consulta avulsa: R$ [VALOR]. Acompanhamento trimestral (3 consultas +
suporte no WhatsApp): R$ [VALOR]. Quero responder o preço sem parecer
tabela fria — a maioria fecha quando entende o acompanhamento.

Tarefa: escreva a resposta para o Direct.

Formato: até 5 linhas. Responda o preço da avulsa direto (nada de
"chama no privado"), apresente o acompanhamento como opção mais
procurada, e termine com uma pergunta sobre o objetivo da pessoa.
```

**O que mudou:** a resposta sai com estratégia embutida — preço transparente + upgrade natural + pergunta que continua a conversa.

Percebeu o padrão dos três casos? O trabalho duro não é escrever bonito — a IA escreve. O trabalho é **dar os fatos**. E é aí que mora um problema: você vai usar IA todo dia, várias vezes ao dia. Vai digitar os fatos do seu negócio toda santa vez?

Não. Você vai escrever uma vez só.

## O Manual do Funcionário

Imagine que você contratou um funcionário excelente, mas com amnésia: toda manhã ele esquece tudo sobre o seu negócio. A solução óbvia seria entregar a ele, toda manhã, uma folha com tudo o que importa: o que vendemos, por quanto, nosso jeito de falar, o que nunca prometer.

A IA é esse funcionário. E essa folha é o **Manual do Funcionário** — um documento único com os fatos do seu negócio, que você cola **no início de toda conversa com a IA**, antes de qualquer prompt. Ele é o "C" de Contexto da fórmula, resolvido de uma vez por todas.

A partir deste capítulo, todos os prompts do livro (e os 77 prompts do bônus) assumem que você colou o Manual antes. É o que transforma resposta genérica em resposta do *seu* negócio.

### O template completo

Copie, preencha e guarde. Linhas que não se aplicam ao seu negócio, apague.

```
MANUAL DO FUNCIONÁRIO — [NOME DO NEGÓCIO]
(Use estas informações como contexto em tudo o que eu pedir nesta
conversa. Não invente nada que não esteja aqui; se faltar informação,
me pergunte.)

O NEGÓCIO
- Nome: [NOME DO NEGÓCIO]
- O que é: [ex: doceria artesanal por encomenda / salão de beleza /
  consultório de nutrição]
- Onde atende: [bairro/cidade, online, delivery, raio de entrega]
- Desde quando existe: [ANO]

O QUE VENDO (com preços)
- [PRODUTO/SERVIÇO 1] — R$ [PREÇO] — [observação: prazo, tamanho, o
  que inclui]
- [PRODUTO/SERVIÇO 2] — R$ [PREÇO] — [observação]
- [PRODUTO/SERVIÇO 3] — R$ [PREÇO] — [observação]
- Mais procurado: [QUAL]

FUNCIONAMENTO
- Horários: [DIAS E HORAS]
- Prazo de entrega/agenda: [ex: encomendas com 48h de antecedência]
- Formas de pagamento: [Pix, cartão, dinheiro; parcelamento?]
- Políticas: [sinal de X% para encomendar; troca em até X dias;
  cancelamento até X horas antes; etc.]

MEU CLIENTE
- Quem é: [idade aproximada, perfil, o que valoriza]
- Como ele fala comigo: [WhatsApp? Direct? formal? cheio de áudio?]
- Por que compra de mim e não do concorrente: [seu diferencial real]

TOM DE VOZ
- 3 palavras que descrevem meu jeito: [ex: acolhedor, direto, alegre]
- Frases que eu falaria: "[EXEMPLO 1]", "[EXEMPLO 2]"
- O que eu NUNCA falaria: [ex: "imperdível!!!", gíria de internet,
  "prezado cliente"]
- Emoji: [uso moderado / não uso / só esses: ...]

PERGUNTAS FREQUENTES (e a resposta certa)
- "[PERGUNTA 1]" → [RESPOSTA CERTA]
- "[PERGUNTA 2]" → [RESPOSTA CERTA]
- "[PERGUNTA 3]" → [RESPOSTA CERTA]

REGRAS DE OURO (o que a IA nunca deve fazer)
- Nunca prometer prazo ou desconto que não está neste manual.
- Nunca inventar preço, ingrediente, técnica ou disponibilidade.
- Nunca dar conselho [médico/jurídico/financeiro — conforme seu ramo];
  nesses casos, orientar a falar comigo.
- Em reclamação ou assunto delicado: rascunhar com calma e me avisar
  que EU devo revisar antes de enviar.

ASSINATURA PADRÃO
- [Como você fecha mensagens: "Um abraço, Maria — Doce Maria 🍰"]
```

### Exemplo preenchido — Doce Maria

Para você ver o tamanho certo (note que é específico sem ser um romance):

```
MANUAL DO FUNCIONÁRIO — DOCE MARIA
(Use estas informações como contexto em tudo o que eu pedir nesta
conversa. Não invente nada que não esteja aqui; se faltar informação,
me pergunte.)

O NEGÓCIO
- Nome: Doce Maria
- O que é: doceria artesanal por encomenda, sem loja física
- Onde atende: bairro Jardim das Flores e região (entrego num raio de
  8 km, taxa R$ 8) — retirada também
- Desde quando existe: 2022

O QUE VENDO (com preços)
- Bolo de pote (ninho c/ morango, chocolate, limão) — R$ 14
- Bolo de festa por kg — R$ 75/kg — encomenda com 5 dias
- Caixa de brigadeiros gourmet (20 un) — R$ 48
- Kit festa básico (bolo 1kg + 30 docinhos) — R$ 140
- Mais procurado: bolo de pote de ninho com morango

FUNCIONAMENTO
- Horários: respondo das 9h às 19h, seg a sáb
- Prazo: bolos de pote com 24h; bolos de festa com 5 dias
- Pagamento: Pix ou dinheiro; encomendas acima de R$ 100 com sinal
  de 50%
- Políticas: cancelamento de encomenda até 48h antes devolve o sinal

MEU CLIENTE
- Mulheres de 25 a 50 anos do bairro; compram para festas de família
  e para presentear
- Falam comigo pelo WhatsApp, tom carinhoso, muitas mandam áudio
- Compram de mim pela massa de bolo molhadinha e porque cumpro prazo

TOM DE VOZ
- Carinhosa, alegre, próxima
- Frases minhas: "feito com carinho, do meu forno pra sua festa",
  "pode deixar comigo!"
- NUNCA falo: "imperdível", "promoção relâmpago", "prezado cliente"
- Emoji: moderado, gosto de 🍰 e 💛

PERGUNTAS FREQUENTES
- "Faz sem lactose?" → Faço sob encomenda com 3 dias, +20% no valor
- "Entrega quando?" → Bolo de pote: amanhã. Bolo de festa: 5 dias
- "Tem pronta entrega?" → Só sextas à tarde, anuncio nos stories

REGRAS DE OURO
- Nunca prometer entrega fora dos prazos acima
- Nunca inventar sabor ou preço
- Reclamação: rascunhar com calma e me avisar para EU revisar

ASSINATURA PADRÃO
- "Um abraço, Maria 🍰 — Doce Maria"
```

### Onde guardar e como usar

1. Crie um documento no **Google Docs** chamado "Manual do Funcionário". (Por quê lá? Sincroniza entre celular e computador, e editar é fácil.)
2. No celular, deixe-o nos **favoritos/com estrela** para achar em 2 toques.
3. **Toda vez** que abrir uma conversa nova com a IA: selecionar tudo → copiar → colar → e só então fazer seu pedido.
4. Nos apps de IA que têm "instruções personalizadas" ou "projetos" (o ChatGPT e o Claude têm), você pode colar o Manual lá uma vez só — aí toda conversa nova já nasce sabendo do seu negócio. Vale os 5 minutos de configuração.

**Manutenção:** mudou preço, horário ou política? Atualize o Manual **no mesmo dia**. Manual desatualizado é a receita para a IA escrever mensagem com preço velho — e adivinha quem o cliente vai cobrar.

## A segunda mensagem é onde a mágica acontece

Prompt bom não é bola de cristal: a primeira resposta raramente vem 100%. A diferença de quem usa IA bem é que **não aceita nem descarta — ajusta**. A IA lembra do que acabou de escrever, então você pode mandar correções curtas, como faria com um estagiário talentoso:

- "Ficou formal demais. Refaz mais leve, como conversa de WhatsApp."
- "Boa, mas corta pela metade."
- "Tira os emojis e troca 'imperdível' por algo que eu diria."
- "Agora me dá 3 variações dessa, mudando só a primeira linha."
- "Reescreve no tom deste exemplo: [colar uma mensagem sua que funcionou]"

Regra prática: **até 3 ajustes**. Se na terceira tentativa ainda está ruim, o problema é o prompt original — volte na fórmula P-C-T-F-E e veja o que faltou (quase sempre, Contexto).

## Sua biblioteca de prompts

Todo prompt que funcionar bem para você é um ativo. Não deixe ele morrer na conversa.

1. Crie um segundo Google Doc: **"Biblioteca de Prompts"**.
2. Seções: Atendimento, Vendas, Conteúdo, Administrativo, Análise (sim, os cinco funcionários deste livro).
3. Quando um prompt der uma resposta ótima, cole o prompt lá com um título ("Follow-up de orçamento — tom leve") e uma linha dizendo quando usar.
4. Comece a biblioteca com os **77 prompts prontos do bônus** deste livro — eles já vêm organizados nessas mesmas seções. Seu trabalho é só ir adaptando os placeholders ao seu negócio e anotando os que mais funcionam.

Em um mês, você terá algo valioso: um caderno de receitas testadas no *seu* negócio, com o *seu* tom. Isso ninguém copia.

## Exercício de 15 minutos (faça antes do próximo capítulo)

Este é o único dever de casa obrigatório do livro, porque tudo daqui em diante depende dele:

1. **(10 min)** Copie o template do Manual do Funcionário para o Google Docs e preencha. Não busque perfeição — preencha o que souber de cabeça. Preços e FAQ você completa amanhã.
2. **(3 min)** Abra sua IA, cole o Manual e mande: `Com base neste manual, que informações importantes sobre o negócio ainda estão faltando ou vagas? Liste até 5 perguntas.` — responda as perguntas dela e atualize o Manual. (Sim: a IA ajudando a melhorar o documento que alimenta a própria IA. Bem-vindo ao truque mais útil deste livro.)
3. **(2 min)** Teste: na mesma conversa, peça `Escreva a mensagem de saudação do meu WhatsApp Business`. Compare com o que você usa hoje.

Se a saudação que saiu te deu vontade de usar — e costuma dar —, você acabou de sentir o que esse livro promete: o seu contexto + a redação da IA + a sua aprovação final.

Agora sim. Vamos contratar o primeiro funcionário.
