# Mapa de Mudanças de Seções · 2º Turno 2026

Mapa interativo (Leaflet) das seções eleitorais alteradas entre o 1º e o 2º turno das Eleições 2026, com informação por **município** e **estado**.

## Estrutura

```
deploy/
├── index.html                      # aplicação (HTML + CSS + JS inline) — ~250 KB
├── assets/
│   └── leaflet/
│       └── leaflet.js              # Leaflet 1.9.4 vendored (offline)
└── data/
    └── municipios.js               # window.MUNICIPIOS_ALTERADOS (malha municipal integral IBGE) — ~12,7 MB
```

- Os **dados de seções** e os **estados** estão embutidos no `index.html`.
- A **malha dos municípios com mudança**, com geometria integral do IBGE, fica em `data/municipios.js`.
- Em 22/10/2026, às 06h28, o TSE informava **326 seções alteradas em 78 municípios**. Esses números mudam a cada atualização.
- **Leaflet** está vendored localmente — o mapa funciona **offline** (basta abrir `index.html` ou servir a pasta).

## Fontes

- **TSE** — Seções eleitorais alteradas (2º turno 2026): `secoes_alteradas_2_turno_2026.csv`.
- **IBGE** — Malha municipal (`Municipios.geojson`, EPSG:4674), filtrada para os municípios com mudança.
- **OpenStreetMap** — tiles do mapa base.

## Observações

- As coordenadas dos *locais de votação* não fazem parte desta versão; o mapa mostra a incidência por município/estado (nº de seções e eleitores).
- O clique no município mostra o resumo quantitativo (seções, eleitores, mudanças de local, zonas, principais destinos).
