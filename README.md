# Mapa de Mudanças de Seções · 2º Turno 2026

Mapa interativo (Leaflet) das seções eleitorais alteradas entre o 1º e o 2º turno das Eleições 2026, com informação por **município** e **estado**.

## Estrutura

```
mapa-secoes-2026/
├── index.html                      # aplicação (HTML + CSS + JS inline)
├── assets/
│   └── leaflet/
│       └── leaflet.js              # Leaflet 1.9.4 vendored (offline)
└── data/
    └── municipios.js               # window.MUNICIPIOS_ALTERADOS (malha municipal integral IBGE)
```

- Os **dados de seções** e os **estados** estão embutidos no `index.html`.
- A **malha dos municípios com mudança**, com geometria integral do IBGE, fica em `data/municipios.js`.
- Em 22/10/2026, às 06h28, o TSE informava **326 seções alteradas em 78 municípios**. Esses números mudam a cada atualização.
- O JavaScript do **Leaflet** está incluído localmente. Mapas base do OpenStreetMap e outros recursos externos dependem de internet; não se garante funcionamento totalmente offline.

## Fontes

- **TSE** — Seções eleitorais alteradas (2º turno 2026): `secoes_alteradas_2_turno_2026.csv`.
- **IBGE** — Malha municipal (`Municipios.geojson`, EPSG:4674), filtrada para os municípios com mudança.
- **OpenStreetMap** — tiles do mapa base.

## Observações

- As coordenadas dos *locais de votação* não fazem parte desta versão; o mapa mostra a incidência por município/estado (nº de seções e eleitores).
- O clique no município mostra o resumo quantitativo (seções, eleitores, mudanças de local, zonas, principais destinos).


## Executar localmente

Com Python 3 instalado:

```bash
git clone https://github.com/RebecaGis/mapa-secoes-2026.git
cd mapa-secoes-2026
python -m http.server 8000
```

Abra http://localhost:8000. O servidor serve os arquivos existentes sem atualizar dados ou alterar a hospedagem.

## Atualização dos dados

Os números apresentados representam a versão dos dados incorporada ao projeto, não uma consulta automática ao TSE em tempo real. Para atualizar, obtenha a fonte oficial, confira seções e municípios e regenere os dados incorporados ao HTML e a malha municipal correspondente. O repositório não inclui uma rotina automatizada de atualização nem os arquivos-fonte citados acima.

Preserve `CNAME` e a estrutura de arquivos ao manter a publicação existente.
