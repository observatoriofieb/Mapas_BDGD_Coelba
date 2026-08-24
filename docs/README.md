# Energia elétrica na Bahia — mapas interativos

Dois mapas estáticos (HTML puro, sem servidor) construídos a partir da **BDGD
2024 da ANEEL** — entrega da Neoenergia Coelba, data-base 31/12/2024.

| Página | O que mostra |
| --- | --- |
| [`index.html`](index.html) | Índice com a descrição dos mapas e a ficha dos dados |
| [`mapa-subestacoes.html`](mapa-subestacoes.html) | As 638 subestações, por posse, com ficha técnica, filtros por tipo e por município |
| [`mapa-consumo-municipio.html`](mapa-consumo-municipio.html) | Mapa de calor do consumo dos 415 municípios, 6 indicadores + tabela exportável |

## Publicar no GitHub Pages

- **Se esta pasta virar o repositório:** Settings → Pages → Source
  *Deploy from a branch* → `main` → **/(root)**.
- **Se ela ficar dentro de um repositório maior:** mesma tela, mas
  escolha **/docs**.

O arquivo `.nojekyll` já está incluído. A publicação leva cerca de um minuto.

## Observações

- As páginas são autocontidas; só as imagens de fundo (mapa base) e a
  biblioteca Leaflet vêm de CDN, então é preciso conexão para visualizar.
- `mapa-consumo-municipio.html` tem ~8 MB porque carrega a malha municipal
  embutida — o primeiro carregamento demora alguns segundos.
- Fonte: dados públicos da ANEEL (BDGD / SIG-R). As ressalvas metodológicas
  estão no índice e nas legendas de cada mapa.
