# Energia elétrica na Bahia — mapas interativos da BDGD

Site estático com dois mapas interativos sobre a rede de distribuição e o
mercado de energia elétrica da Bahia, construídos a partir da **BDGD 2024 da
ANEEL** (Base de Dados Geográfica da Distribuidora, entrega da Neoenergia
Coelba, data-base 31/12/2024).

**Site publicado:** https://SEU-USUARIO.github.io/SEU-REPOSITORIO/

## Conteúdo

Tudo o que é versionado está em [`docs/`](docs), a pasta servida pelo GitHub
Pages:

| Página | O que mostra |
| --- | --- |
| `index.html` | Índice, com a descrição dos mapas e a ficha metodológica dos dados |
| `mapa-subestacoes.html` | As 638 subestações da base, classificadas por posse (cor **e** forma, paleta segura para daltonismo), com tensão, potência, energia, mercado atendido e ficha técnica completa. Filtros por tipo e por município |
| `mapa-consumo-municipio.html` | Mapa de calor do consumo dos 415 municípios atendidos, com 6 indicadores alternáveis e tabela ordenável, filtrável e exportável em CSV |

## Números

| | |
| --- | --- |
| Subestações | 638 · 6.302 MVA de transformação · 1.486 alimentadores |
| Mercado | 7,33 milhões de unidades consumidoras · 22.102 GWh/ano (corrigido) |
| Cobertura | 415 municípios (a Coelba atende quase toda a Bahia; Jandaíra e Rio Real ficam com a Sulgipe) |

## Publicação

`Settings → Pages → Source: Deploy from a branch → main → /docs`.
O arquivo `docs/.nojekyll` já está incluído.

## Reprodução

O processamento roda sobre a geodatabase original da BDGD, que **não é
versionada** (~9 GB; é dado público, baixável no
[Portal de Dados Abertos da ANEEL](https://dadosabertos.aneel.gov.br/dataset/base-de-dados-geografica-da-distribuidora-bdgd)).
Os scripts Python (GeoPandas, Folium, Leaflet) que geram os mapas também ficam
fora deste repositório — veja o `.gitignore` para incluí-los.

## Ressalvas metodológicas

- A energia é anualizada pela soma de `ENE_01..ENE_12`; o município é o do
  ponto de conexão, o que desloca grandes clientes para onde está o ramal.
- No mapa de consumo, 186 registros de baixa tensão incompatíveis com a classe
  de tensão (acima de 657 MWh/ano) foram removidos — 1,57% do consumo, em 80
  municípios. As versões bruta e corrigida ficam lado a lado na tabela.
- O domínio do campo `POS` (posse da subestação) não vem descrito na BDGD: os
  rótulos foram inferidos dos próprios dados e o código original aparece sempre
  no mapa.
- O campo `POT_INST` das unidades geradoras tem erro de unidade na origem,
  sinalizado onde afeta o resultado.

Dados públicos da ANEEL / SIG-R.
