# Tipografia da loja (12/11/2026)

A loja passou a usar a fonte do logo. Esta mudança foi aplicada direto no HTML publicado;
**o gerador (`loja.py`) ainda precisa receber a mesma mudança**, senão a próxima geração volta para a fonte antiga.

## Regra

- **Montserrat** (a fonte do logo): títulos em peso 800, textos, rótulos, menu, preços e números.
- **Instrument Serif itálica**: só nos destaques (`<em>` dos títulos), na frase do signo, no arquétipo, na faixa que corre e na legenda da foto.
- A Instrument Sans saiu da loja (continua só no estilo de formatura que já a usava).

## O que portar para o `loja.py`

1. Link das fontes: trocar `family=Instrument+Sans:wght@400;500;600;700` por
   `family=Montserrat:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,400`.
2. No `:root`: `--sans` vira `'Montserrat', system-ui, -apple-system, 'Segoe UI', sans-serif` e entra `--tit` com o mesmo valor. `--serif` continua Instrument Serif.
3. Em `.lj-topo, .lj-rodape` e `.trilha`: trocar 'Instrument Sans' por 'Montserrat'.
4. Colar o bloco abaixo no fim do CSS do sistema novo (depois das media queries):

```css
/* tipografia da marca: Montserrat (a fonte do logo) nos títulos e textos; Instrument Serif itálica só nos destaques */
body { font-size:16px; line-height:1.6; }
.eti { font-size:11.5px; letter-spacing:.2em; }
h1, h2, h3 { font-family:var(--tit); font-weight:800; letter-spacing:-.035em; line-height:1; }
h1 em, h2 em, h3 em, .lj-rodape .marca em { font-family:var(--serif); font-style:italic; font-weight:400; font-size:1.14em; letter-spacing:-.02em; line-height:.8; }
.gg { font-size:clamp(44px, 13vw, 176px); letter-spacing:-.05em; line-height:.92; }
.ab h1 { line-height:1.12; margin-bottom:.12em; }
.g { font-size:clamp(34px, 6.4vw, 98px); letter-spacing:-.04em; }
.m { font-size:clamp(28px, 4vw, 58px); }
.p { font-size:clamp(22px, 2.5vw, 34px); }
.lead { font-size:clamp(17px, 1.5vw, 20px); line-height:1.5; }
.bt { font-size:15px; }
@media (max-width:430px) { .bt { white-space:normal; text-align:center; line-height:1.25; padding:12px 24px; max-width:100%; } }
.valor { font-family:var(--tit); font-weight:800; font-size:clamp(34px, 4vw, 54px); letter-spacing:-.04em; }
.nums b { font-family:var(--tit); font-weight:800; font-size:clamp(58px, 9vw, 150px); letter-spacing:-.06em; }
.rol .nome { font-family:var(--tit); font-weight:800; font-size:clamp(30px, 5vw, 78px); line-height:1; letter-spacing:-.045em; }
.cat a .nome { font-size:clamp(32px, 6.2vw, 100px); }
.pg h3 { font-size:clamp(20px, 1.9vw, 26px); line-height:1.12; letter-spacing:-.025em; }
.cart h3 { font-size:clamp(18px, 1.6vw, 24px); line-height:1.12; letter-spacing:-.025em; }
summary::after { font-family:var(--tit); font-weight:300; }
.prox .g { font-family:var(--tit); font-weight:800; }
.barra b { font-family:var(--tit); font-weight:800; font-size:22px; letter-spacing:-.03em; }
.lj-rodape .marca { font-family:var(--tit); font-weight:800; font-size:clamp(40px, 10vw, 150px); line-height:.95; letter-spacing:-.05em; }
@media (max-width:760px) { .lj-nav a { font-size:11px; letter-spacing:.04em; } }
@media (max-width:350px) { .lj-nav a { font-size:10.5px; letter-spacing:.01em; } }
```

5. Nas páginas de estilo de formatura (que só têm cabeçalho e rodapé da loja), colar:

```css
/* tipografia da marca no cabeçalho e rodapé da loja */
.lj-rodape .marca { font-family:'Montserrat', system-ui, -apple-system, 'Segoe UI', sans-serif; font-weight:800; font-size:clamp(40px, 10vw, 150px); line-height:.95; letter-spacing:-.05em; }
.lj-rodape .marca em { font-family:'Instrument Serif', Georgia, serif; font-style:italic; font-weight:400; font-size:1.14em; letter-spacing:-.02em; line-height:.8; }
@media (max-width:760px) { .lj-nav a { font-size:11px; letter-spacing:.04em; } }
@media (max-width:350px) { .lj-nav a { font-size:10.5px; letter-spacing:.01em; } }
```

6. Nome gigante do hotsite (`.ab h1.gg`): o divisor do `calc()` é a largura do texto em em, e mudou com a fonte.
   Na Montserrat 800 com `letter-spacing:-.05em`, medir a largura do nome a 100px, dividir por 100 e multiplicar por 1,03.
   O teto em px passa a ser `min(teto antigo, 1208 / divisor)` para o nome não passar da coluna em telas largas.
   Valores atuais: ver o `style` de cada `h1` publicado.

Conferido em 320, 360, 390, 768, 1280 e 1920 px nas 50 páginas: sem rolagem lateral e nomes dentro da tela.
