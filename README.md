# Energia elétrica na Bahia — mapas interativos da BDGD

**Observatório da Indústria — Federação das Indústrias do Estado da Bahia (FIEB)**

Site estático com dois mapas interativos sobre a rede de distribuição e o
mercado de energia elétrica da Bahia, **com dados de 2024**. A ferramenta apoia
o diagnóstico do sistema elétrico baiano por formuladores de política e pelo
setor produtivo, com transparência metodológica total.

## A fonte

A **BDGD — Base de Dados Geográfica da Distribuidora** é o retrato
georreferenciado do sistema elétrico de uma concessionária. Todas as
distribuidoras do país são obrigadas a entregá-la anualmente à ANEEL, no formato
do Módulo 10 do PRODIST, que estrutura o Sistema de Informação Geográfica
Regulatório (SIG-R). É a base que a agência usa para fiscalizar a rede, apurar
perdas e instruir revisões tarifárias, e é informação pública.

Não é amostra nem agregado: é o cadastro completo, ativo por ativo e cliente por
cliente — cada subestação, alimentador, transformador e trecho de rede com
localização e características técnicas; cada unidade consumidora com classe,
tensão, situação e consumo mês a mês.

A distribuidora aqui é a **Neoenergia Coelba** (Companhia de Eletricidade do
Estado da Bahia, código 47 na ANEEL), concessionária de 415 dos 417 municípios
baianos — Jandaíra e Rio Real são atendidas pela Sulgipe.

**Os dados são de 2024**: entrega com data-base **31/12/2024** (arquivo `V11`,
gerado em 02/09/2025). Os ativos são a posição da rede em 31/12/2024 e a energia
é a soma dos doze meses de 2024. Não há mistura de anos.

**Site publicado:** https://observatoriofieb.github.io/Mapas_BDGD_Coelba/

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
