# Catálogo de visualizaciones · Visual Modeling UPY

Gráficas, mapas y escenas 3D/AR que propuso cada uno de los 9 equipos, con su fuente, su estado y de dónde salen sus datos. Lo mantiene el Data Visualization Team como base para la narrativa común del dashboard integrado y de la versión impresa.

| Archivo | Para qué |
|---|---|
| `catalogo_visualizaciones.json` | Fuente única: equipos y visuales. Todo lo demás se genera desde aquí |
| `index.html` | Catálogo web con matriz equipo × tipo de gráfica y filtros |
| `imprimible.html` · `catalogo_visualizaciones.pdf` | Versión impresa (borrador, tamaño carta) con QR a la versión web |
| `img/` | Figuras y capturas de los equipos, con crédito y enlace a su repositorio |
| `scripts/` | Generador del sitio y del PDF |

## Regenerar

```bash
pip install -r requirements.txt
python scripts/generar_catalogo.py --pdf
```

El PDF necesita Node y Playwright con Chromium. La URL del QR se cambia con la variable `CATALOGO_URL`.

## Cómo agregar o corregir un visual

Edita `catalogo_visualizaciones.json` y vuelve a generar. Cada visual lleva:

- `eq`: número de equipo.
- `tipo`: `Barras`, `Línea`, `Mapa`, `Heatmap`, `Distribución`, `Radar`, `Red / flujo`, `KPI / tabla` o `3D / AR`.
- `estado`: `imagen`, `interactivo`, `texto` o `candidato`.
- `datos`: `real` (lee un archivo del repo del equipo), `fijo` (cifras escritas a mano), `simulado` o `sin_datos`.
- `ref`: ruta del archivo dentro del repo del equipo.
- `img`: opcional, ruta dentro de `img/`.

El generador se detiene si un tipo, estado o imagen no es válido.

## Equipos

| # | Proyecto | Repositorio |
|---|---|---|
| 1 | Mérida, Ciudad Esponja | [joseeangel0/merida-ciudad-esponja](https://github.com/joseeangel0/merida-ciudad-esponja) |
| 2 | Del Mundo a la Esquina | [valnix140405/visual_modeling](https://github.com/valnix140405/visual_modeling) |
| 3 | El Viaje de la Resiliencia | [RusselKu/Mexico-DataViz-by-UPY](https://github.com/RusselKu/Mexico-DataViz-by-UPY) |
| 4 | Sentir la Calle | [Rivaldo2309030/Visual-Modeling-For-Information](https://github.com/Rivaldo2309030/Visual-Modeling-For-Information) |
| 5 | Percepción de inseguridad en Yucatán | [ldpl3012/percepcion-inseguridad-yucatan](https://github.com/ldpl3012/percepcion-inseguridad-yucatan) |
| 6 | Datos viales de Mérida | [jonavm/merida-datos-viales](https://github.com/jonavm/merida-datos-viales) |
| 7 | Water situation | [Audileleach/Water_situation_Sources](https://github.com/Audileleach/Water_situation_Sources) |
| 8 | Del tren a la calle | [ezraidenn/del-tren-a-la-calle](https://github.com/ezraidenn/del-tren-a-la-calle) |
| 9 | Mérida for Sale | [BradRobles/M-rida-for-Sale](https://github.com/BradRobles/M-rida-for-Sale) |

Corte de la revisión: 2026-11-24.

## Publicación

GitHub Pages publica la rama `main` (carpeta raíz) en cada push: *Settings → Pages → Deploy from a branch*. El archivo `.nojekyll` evita que GitHub procese el sitio con Jekyll.
