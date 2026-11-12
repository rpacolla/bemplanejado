# Arquitetura da loja (12/11/2026)

Aplicada direto no HTML publicado. **O gerador (`loja.py`) ainda precisa receber a mesma mudança**, senão a próxima geração desfaz tudo. Ver também `TIPOGRAFIA.md`.

## Regra

Cada botão do menu abre uma **lista de temas**. Cada tema tem a sua página. Dentro do tema ficam os produtos.

| Botão | Página | Temas hoje | Página do tema |
|---|---|---|---|
| Planners | `/planners/` | Zodíaco | `/planners/zodiaco/` (lista dos 12 signos) |
| Cadernos | `/cadernos/` | Zodíaco | `/cadernos/zodiaco/` (lista dos 12 signos) |
| Formatura | `/kits/formatura/` | Missão Cumprida, Clássica, Editorial, Cor, Radiante | página de cada tema |
| Kits | `/kits/` | só conjuntos: Kit do signo e Formatura quatro temas | |

- Os endereços dos produtos não mudaram (`/planners/leao/`, `/kits/formatura/classica/`, `/kits/missao-cumprida/`).
- Tema novo (ex.: Festas religiosas em Planners, Aves do Brasil em Cadernos): entra como mais um item na lista `rol cat` da página do botão e ganha a pasta `/<botao>/<tema>/`.
- Trilhas: `Início / Planners / Zodíaco / Leão`; `Início / Formatura / Clássica`; `Início / Formatura / Missão Cumprida`.
- Links soltos que levavam à lista de signos ("Escolher meu signo", "Ver o caderno") apontam para `/planners/zodiaco/` e `/cadernos/zodiaco/`. Menu e rodapé apontam para a raiz do botão.

## Formatura

- A página é só a lista de temas, todos no mesmo formato de cartão. Sem faixa de ano escolar e sem a ideia de "quatro estilos".
- Missão Cumprida é um tema de formatura (R$ 29,90, por ter mais peças). Clássica, Editorial, Cor e Radiante: **R$ 19,90** cada.
- O conjunto dos quatro (`/kits/formatura/4-estilos/`, R$ 49,90) aparece só em Kits e no rodapé interno das páginas de tema. A conta passou a ser `4 × R$ 19,90 = R$ 79,60`, e "menos que o preço de dois" virou "de três".

## Pendências fora do site

- Trocar o preço dos quatro kits na Hotmart para R$ 19,90 (o site só mostra o preço; quem cobra é a Hotmart).
- Decidir se o conjunto dos quatro continua em R$ 49,90.
