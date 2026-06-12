# LANÇAMENTO — Funcionários Digitais (Hotmart)

> Tempo total estimado da sua parte: **2h30 a 3h30, uma única vez.**
> Tudo que está em `ebook/`, `bonus/` e `vendas/` já está pronto — você só publica.

## Visão geral do funil

```
Afiliados (60% de comissão) ──→ Página de vendas ──→ Checkout Hotmart (R$ 97)
        ↑                                                    │
  Kit de afiliado pronto                          Entrega automática (PDF + bônus)
  (vendas/kit-afiliado.md)                        E-mails pós-venda automáticos
```

A Hotmart cuida de: pagamento (Pix/cartão/boleto), nota, entrega do arquivo,
reembolso de 7 dias e repasse ao afiliado. Por isso o negócio "roda sozinho".

## FASE 1 — Gerar os arquivos finais (15 min)

1. Gere o ebook em HTML único:
   ```bash
   cd ventures/01-funcionarios-digitais/ebook
   node build-ebook.mjs
   ```
   Isso cria `funcionarios-digitais.html`.
2. Abra o HTML no navegador → **Imprimir → Salvar como PDF** (A4, margens padrão).
   Esse é o arquivo principal do produto: `funcionarios-digitais.pdf`.
3. Faça o mesmo com os bônus (são Markdown; cole no Google Docs e exporte PDF, ou
   peça ao Claude numa próxima sessão para gerar HTML deles também):
   - `bonus/77-prompts-prontos.md` → PDF
   - `bonus/5-fluxos-de-automacao.md` → PDF
   - `bonus/checklist-7-dias.md` → PDF
   - `bonus/planilha-roi.csv` (entregar como está) + `planilha-roi-instrucoes.md` → PDF
4. Capa: crie no Canva (busque template "capa ebook" e use o título; 10 min) ou peça
   ao Claude com o MCP do Canva conectado. Dimensão boa: 1600×2560 px.

## FASE 2 — Conta e produto na Hotmart (45–60 min)

1. Crie conta em https://hotmart.com (pessoa física funciona; CPF + dados bancários).
2. "Meus produtos" → "Cadastrar produto" → tipo **E-book/Arquivo**.
   - Nome: `Funcionários Digitais — Agentes de IA para Pequenos Negócios`
   - Categoria: Negócios e Carreira (ou Marketing Digital)
   - Descrição: use o início de `vendas/pagina-de-vendas.md`
   - Upload: PDF principal + os 4 bônus (a Hotmart entrega tudo junto)
3. Preço: **R$ 97**. Garantia: **7 dias** (padrão).
4. Página de vendas: monte com a Hotmart Pages usando `vendas/pagina-de-vendas.md`
   seção por seção (já está na ordem certa: hero → dor → mecanismo → entregáveis →
   bônus → para quem é → garantia → FAQ → CTA).
5. Envie para revisão da Hotmart (leva ~1–3 dias úteis; a copy já foi escrita para
   passar — sem promessa de renda, sem depoimento inventado).

## FASE 3 — Programa de afiliados (30 min) ← AQUI MORA A DISTRIBUIÇÃO

1. No produto → "Afiliação": **ativar**, modo "com aprovação".
2. Comissão: **60%** (alto de propósito: você quer que afiliado profissional escolha
   o SEU produto no marketplace). Atribuição: último clique, cookie 60 dias.
3. Marque "disponibilizar materiais para afiliados" e suba o conteúdo de
   `vendas/kit-afiliado.md` (copies, descrições de criativos, e-mails prontos).
4. Na descrição para afiliados, escreva: nicho quente (IA para negócios), comissão
   60%, kit completo de criativos pronto, página de vendas sem promessas proibidas
   (= conta de anúncio do afiliado não corre risco).
5. **Aprove afiliados em até 24 h** (rotina de monitoramento). Recuse perfis que
   prometem renda em anúncio — protegem você de banimento.

## FASE 4 — Tração inicial sem audiência (1–2 h, opcional mas recomendado)

Avaliações e primeiras vendas atraem afiliados. Três alavancas de custo zero:

1. **Preço de lançamento R$ 29,90 por 7 dias** para gerar volume inicial e avaliações
   (sobe para R$ 97 depois — escassez REAL, pode comunicar).
2. Poste em 3–5 grupos (Facebook/WhatsApp/Telegram) de MEI/empreendedorismo dos quais
   você participe, com tom de ajuda, não de spam (há copy pronta no kit de afiliado).
3. E-mails pós-venda (`vendas/emails-pos-venda.md`): cadastre na automação da Hotmart
   (ListBoss/Zapier) ou envie manualmente nos primeiros dias. O e-mail D+10 pede
   avaliação — avaliação ≥ 4,5 é o que faz afiliado confiar no produto.

## Alternativa: Kiwify

Mesmo processo, taxas similares, aprovação às vezes mais rápida. Pode publicar nas
duas (não é exclusivo). Comece pela Hotmart pelo marketplace de afiliados maior.

## Checklist final

- [ ] PDF principal gerado e revisado (passe o olho em 3 capítulos)
- [ ] 4 bônus em PDF/CSV
- [ ] Capa criada
- [ ] Produto cadastrado, preço R$ 97, garantia 7 dias
- [ ] Página de vendas montada com a copy pronta
- [ ] Afiliação ativa, 60%, kit de afiliado anexado
- [ ] Produto aprovado pela Hotmart
- [ ] (Opcional) preço de lançamento + posts iniciais
- [ ] Rotina semanal de 30 min agendada (aprovar afiliados, responder, monitorar)
