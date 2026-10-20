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

- Os **dados de seções** (441 registros) e os **estados** estão embutidos no `index.html`.
- A **malha municipal** (106 municípios com mudança, geometria integral do IBGE) fica em `data/municipios.js`.
- **Leaflet** está vendored localmente — o mapa funciona **offline** (basta abrir `index.html` ou servir a pasta).

## Publicação

Basta servir a pasta `deploy/` em qualquer host estático.

### GitHub Pages

1. Crie um repositório e envie o conteúdo de `deploy/` (os arquivos podem ficar na raiz ou em `docs/`).
2. Em *Settings → Pages*, aponte *Source* para a branch e a pasta onde estão os arquivos.
3. O mapa ficará em `https://<usuario>.github.io/<repo>/`.

### Netlify / Vercel

Arraste a pasta `deploy/` (ou aponte o projeto para ela). Não há build: é 100% estático.

### Servidor qualquer / intranet

Copie a pasta `deploy/` e sirva com qualquer servidor estático, por exemplo:

```bash
cd deploy && python -m http.server 8080
```

Depois abra `http://localhost:8080`. Também funciona abrindo `index.html` direto no navegador (file://).

## Rebuild

O gerador está em `work/build_leaflet.py`. Para regerar o pacote:

```bash
python work/build_leaflet.py --deploy
```

Sem `--deploy`, ele gera o arquivo único `outputs/mapa_secoes_2_turno_2026_v2.html` (com a malha embutida).

## Fontes

- **TSE** — Seções eleitorais alteradas (2º turno 2026): `secoes_alteradas_2_turno_2026.csv`.
- **IBGE** — Malha municipal (`Municipios.geojson`, EPSG:4674), filtrada para os municípios com mudança.
- **OpenStreetMap** — tiles do mapa base.

## Observações

- As coordenadas dos *locais de votação* não fazem parte desta versão; o mapa mostra a incidência por município/estado (nº de seções e eleitores).
- O clique no município mostra o resumo quantitativo (seções, eleitores, mudanças de local, zonas, principais destinos).
