# Coches.net · UX Audit / Benchmark 2026

> Confidencial · Erretres × Adevinta Motor · Mayo 2026

Benchmark UX completo de Coches.net frente a 32 referencias del mercado: 10 competidores directos, 11 indirectos y 11 aspiracionales. Auditoría visual, estratégica y accionable.

**[→ Abrir el deck (172 slides)](./index.html)**

## Estructura

```
.
├── index.html                              ← El deck, 172 slides editables
├── assets/
│   ├── screenshots/                        ← 102 capturas reales por marca/sección
│   └── fonts/                              ← Espacio para PP Neue Montreal local
├── exports/
│   ├── CNET_Benchmark_UX_2026.pdf          ← 172 páginas vectoriales para Figma
│   ├── slides-png/                         ← 172 PNGs @2x (1280×720)
│   ├── slides-svg/                         ← 172 SVGs editables
│   ├── CNET_Benchmark_UX_2026_Figma.zip    ← Todo lo anterior empaquetado
│   └── README.md                           ← Instrucciones de import a Figma
└── README.md                               ← (este archivo)
```

## Capítulos

| Cap | Bloque | Slides |
|---|---|---|
| 00 | Cover + Introducción | 7 |
| 01 | Diagnóstico interno Coches.net | 5 |
| 02 | Benchmark directo (10 marcas) | 51 |
| 03 | Benchmark indirecto (11 marcas) | 44 |
| 04 | Benchmark aspiracional (11 marcas) | 33 |
| 05 | Future patterns (IA, semantic, etc.) | 4 |
| 06 | Conclusiones (principios, territorios, roadmap) | 8 |
| – | Logo walls + insights de cierre + mapa competitivo | 20 |
| **Total** | | **172** |

## Cómo iterar localmente

```bash
git clone https://github.com/acabrera-bit/coches-net-ux-audit.git
cd coches-net-ux-audit
# Abrir el deck en el navegador
open index.html
```

Para servir vía HTTP (recomendado para que se carguen las capturas correctamente):

```bash
python3 -m http.server 8000
# Ir a http://localhost:8000
```

## Cómo regenerar los exports

Requiere Node 18+ y Playwright instalado:

```bash
cd /tmp && mkdir shotter && cd shotter
npm init -y && npm install playwright dom-to-svg esbuild
npx playwright install chromium
# Copia los scripts desde el chat o se regeneran al volver a pedir
node exporter.js          # → PDF vectorial multi-página
node export_pngs.js       # → 172 PNGs @2x
node export_svgs2.js      # → 172 SVGs vectoriales
```

## Stack técnico

- **HTML/CSS modular**, sin frameworks, totalmente portable.
- **PP Neue Montreal Medium** vía Fontshare (Neue Montreal) con fallback Inter.
- **Auto-scale** del slide 1280×720 al viewport con CSS `zoom`.
- **PDF export ready** vía `window.print()` o Playwright `page.pdf()`.

## Equipo

Erretres · The Strategic Design Co. · [hola@erretres.com](mailto:hola@erretres.com)
