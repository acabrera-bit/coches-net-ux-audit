# CNET Benchmark UX 2026 · Entregables para Figma

Erretres × Adevinta Motor · Mayo 2026

---

## ¿Qué hay en esta carpeta?

```
exports/
├── CNET_Benchmark_UX_2026.pdf      ← 172 páginas vectoriales, 1280×720 c/u
├── slides-png/                      ← 172 PNGs hi-res (1280×720 @2x retina)
├── slides-svg/                      ← 172 SVGs vectoriales (si el export tuvo éxito)
└── README.md                        ← este archivo
```

---

## Importar a Figma como editable

### Opción A · PDF vectorial (recomendada, gratis, sin plugins)

1. Abre **Figma** (web o desktop).
2. Arrastra `CNET_Benchmark_UX_2026.pdf` directamente al canvas.
3. Figma generará **un frame por página** (172 frames de 1280×720), conservando:
   - **Texto editable** — todos los títulos, copy y anotaciones siguen siendo capas `Text` con tipografía PP Neue Montreal Medium.
   - **Vectores** — líneas, formas y rules como `Vector` editables.
   - **Imágenes** — las capturas de los sitios como `Image fill` reemplazables.
   - **Colores** — paleta Erretres (azul `#1F3FFF`, ink `#0A0A0B`, bone `#F2EFEA`, signal `#FFE500`) como solid fills.
4. Reordena, edita y construye sobre la base.

**Limitaciones del PDF:**
- Algunos efectos (mix-blend-mode, mask-image) pueden aplanarse a imagen.
- Las anotaciones tipo sticky-note se importan como rectángulos + texto separados.

### Opción B · SVG por slide (máxima editabilidad por capa)

1. Abre Figma.
2. Arrastra todos los archivos de `slides-svg/` al canvas a la vez (o selecciónalos y `Cmd+V`).
3. Cada SVG llega como un frame independiente con todas las capas (text, rect, image) editables.

Útil si el PDF aplana algo concreto y quieres recuperar esa capa puntual.

### Opción C · PNGs hi-res (no editable de capas, pero pixel-perfect)

1. Carpeta `slides-png/`.
2. Cada PNG es 1280×720 @2x (2560×1440 reales).
3. Útil para:
   - Previsualizaciones rápidas para Keynote/PowerPoint.
   - Compartir con stakeholders por WhatsApp/Slack/email sin abrir el deck.
   - Subir a Figma como **un único frame por slide** (pixel-perfect, no editable).

### Opción D · Plugin `html.to.design` (alternativa pago)

Si quieres reconstruir el deck en Figma desde cero con capas 100% nativas:
1. Instala el plugin `html.to.design` desde la Figma Community.
2. Sirve `benchmark/index.html` con `python3 -m http.server 8000` en el directorio padre.
3. En el plugin pega `http://localhost:8000/benchmark/index.html` y deja que importe.
4. Necesitas tier gratuito para algunas páginas; el resto requiere suscripción.

---

## Nombres de archivo

```
slide-001.png                                  ← deck cover
slide-002.png                                  ← capítulo 00 cover
…
slide-014_autoscout24-cover.png                ← brand cover AutoScout24
slide-015_autoscout24-home.png                 ← análisis Home AutoScout24
slide-016_autoscout24-plp.png                  ← análisis Listado
slide-017_autoscout24-pdp.png                  ← análisis Ficha
slide-018_autoscout24-editorial.png            ← análisis Editorial
…
```

Convención: `slide-{NNN}[_{marca}-{seccion}].png|svg`

---

## Estructura del deck (172 slides)

| Cap | Bloque | Slides |
|---|---|---|
| 00 | Cover + Introducción | 7 |
| 01 | Diagnóstico interno Coches.net | 5 |
| 02 | Benchmark directo (10 marcas × 4-7 slides) | 51 |
| 03 | Benchmark indirecto (11 marcas × 3-4 slides) | 44 |
| 04 | Benchmark aspiracional (11 marcas × 3-4 slides) | 33 |
| 05 | Future patterns (IA, semantic search, etc.) | 4 |
| 06 | Conclusiones (principios, territorios, hipótesis, roadmap) | 8 |
| – | Logo walls, mapas competitivos, insights de cierre, quote slide | 20 |
| **Total** | | **172** |

---

## Volver a generar los exports

Si modificas `benchmark/index.html` y quieres re-exportar:

```bash
cd /tmp/shotter
node exporter.js        # PDF + intento PNG combinado
node export_pngs.js     # solo PNGs hi-res
node export_svgs2.js    # solo SVGs (requiere bundle dom-to-svg)
```

---

## Notas técnicas

- **Tipografía**: PP Neue Montreal Medium (Fontshare fallback). Para edición exacta en Figma, instala PP Neue Montreal localmente o usa el fallback Inter que Figma resolverá automáticamente.
- **Capturas reales**: 102 screenshots en `benchmark/assets/screenshots/<marca>/<seccion>.png`. Tomadas con Playwright + Chromium a viewport 1440×900, locale es-ES.
- **Sitios bloqueados** (Akamai bot-detection): Tesla, Idealista, Spoticar, parcialmente Zillow y Chrono24 — sustituidas con thum.io como fallback.
- **Fuente original**: `benchmark/index.html` (3.500 líneas, 1 fichero portable). Puede regenerarse / iterarse sobre él.
