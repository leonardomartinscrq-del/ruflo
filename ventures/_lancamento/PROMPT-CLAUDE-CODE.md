# PROMPT MESTRE — Colar no Claude Code local (com acesso a navegador)

> Cole TODO o bloco abaixo numa sessão do Claude Code rodando NA SUA MÁQUINA
> (terminal ou extensão Claude in Chrome), com Hotmart e Gumroad já logados no navegador.
> Este repositório já contém todos os arquivos referenciados.

---

Você é meu operador de lançamento. As contas Hotmart e Gumroad já estão logadas no meu Chrome. Execute o lançamento do meu ebook na Hotmart e do meu pack na Gumroad seguindo EXATAMENTE os passos abaixo. Antes de qualquer ação irreversível (definir preço, publicar, enviar para revisão), me mostre o que vai fazer e peça confirmação. Trabalhe um passo de cada vez e tire screenshot após cada tela para eu acompanhar.

## CONTEXTO / ARQUIVOS (já existem neste repositório)
- Ebook (HTML p/ virar PDF): `ventures/_lancamento/funcionarios-digitais.html`
- Bônus (zip): `ventures/_lancamento/bonus-funcionarios-digitais.zip`
- Pack dev (zip): `ventures/_lancamento/claude-code-power-pack.zip`
- Copy de vendas do ebook: `ventures/01-funcionarios-digitais/vendas/pagina-de-vendas.md`
- Sequência de e-mails: `ventures/01-funcionarios-digitais/vendas/emails-pos-venda.md`
- Kit de afiliado: `ventures/01-funcionarios-digitais/vendas/kit-afiliado.md`
- Listing Gumroad: `ventures/02-claude-code-power-pack/sales/gumroad-listing.md`

## PASSO 0 — Gerar o PDF do ebook
Abra `ventures/_lancamento/funcionarios-digitais.html` no Chrome, use Imprimir → Salvar como PDF (margens padrão, com gráficos de fundo), salve como `funcionarios-digitais.pdf`. Se conseguir fazer isso via linha de comando (ex.: headless chrome `--print-to-pdf`), pode fazer direto.

## PASSO 1 — HOTMART (app.hotmart.com)
Crie o produto:
- Tipo: **E-book**
- Nome: **Funcionários Digitais — O Guia Prático de Agentes de IA para Pequenos Negócios**
- Categoria: **Negócios e Carreira** (ou Empreendedorismo Digital)
- Idioma: **Português (Brasil)**
- Preço: **R$ 97,00** · pagamento único · moeda BRL
- Garantia: **7 dias**
- Descrição: cole o conteúdo de `pagina-de-vendas.md` na ordem das seções [HERO] → [DOR] → [VIRADA] → [MECANISMO] → [O QUE VOCÊ RECEBE] → [FAQ]
- Arquivo principal: `funcionarios-digitais.pdf`
- Material complementar: `bonus-funcionarios-digitais.zip`

## PASSO 2 — HOTMART: Programa de Afiliados (CRÍTICO)
- Ative o programa de afiliados
- Comissão: **60%**
- Atribuição: último clique · Cookie: **60 dias**
- Aprovação: automática
- **Disponibilizar no Mercado de Afiliados (vitrine): SIM** ← isto é o que traz vendas
- Suba o conteúdo de `kit-afiliado.md` como material para afiliados

## PASSO 3 — HOTMART: E-mails pós-venda
Configure a automação de e-mail com a sequência de 5 e-mails de `emails-pos-venda.md` (D0, D+2, D+5, D+10, D+21).

## PASSO 4 — HOTMART: Enviar para revisão
Envie o produto para análise da Hotmart. Me avise o status final.

## PASSO 5 — GUMROAD (gumroad.com)
Crie o produto:
- Tipo: Digital product
- Nome: **Claude Code Power Pack — 30 production-grade subagents, 10 skills, 8 hook recipes, 4 CLAUDE.md templates**
- Preço: **$14**
- Descrição: cole a "Full Description" inteira de `gumroad-listing.md`
- Conteúdo (upload): `claude-code-power-pack.zip`
- Slug: `claude-code-power-pack`
- Publique (Publish)

## AO FINAL
Me entregue: link público do produto na Hotmart, link de afiliação, e o link público do produto na Gumroad. Liste qualquer passo que ficou pendente de revisão da plataforma.
