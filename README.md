# Tablero de Ratings — Coderhouse

Tablero estático que lee el Google Sheet público en vivo desde el navegador.
No necesita backend, ni base de datos, ni variables de entorno.

## Vistas
- **Esta semana vs semana anterior** (rating, respuestas, CC nuevo/viejo).
- **Ratings por curso**: selector de curso, comisiones y cuáles tienen el CC nuevo.
- **CC nuevo vs viejo**: tendencia semanal global + por curso.
- **Prioridad · Top vendidos**: cruce del top 5 más vendidos con su rating + mejor/peor.
- **Temática · Live Sessions**: inscriptos totales vs activos por temática.

## Es dinámico, semana a semana
Cada vez que abrís o tocás **↻ Recargar**, vuelve a leer el Sheet y recalcula
todo agrupado por semana (lunes a domingo). Pensado para mirar cada lunes.

## Filtro de fechas
Arriba hay un selector de **Período** (Todo / 4 / 8 / 12 / 26 semanas /
Personalizado con rango desde–hasta) que afecta los KPIs, las tendencias y las
prioridades.

## Subir a Vercel
Opción más simple (sin instalar nada):
1. Entrá a https://vercel.com e iniciá sesión.
2. **Add New… → Project → Deploy** (o arrastrá esta carpeta en vercel.com/new).
3. Subí la carpeta `tablero-coderhouse` (que contiene este `index.html`).
4. Listo: Vercel te da una URL pública.

Con Vercel CLI:
```bash
npm i -g vercel
cd tablero-coderhouse
vercel        # seguí los pasos; framework: "Other"
vercel --prod # para publicar
```

## Configuración editable
Dentro de `index.html`, arriba de todo en el `<script>`:
- `SHEET_ID`: el ID del Google Sheet.
- `TOP_SELLING_COURSES`: la lista del top 5 más vendidos (match por texto).

## Notas
- El Sheet tiene que seguir siendo **público** (cualquiera con el link puede ver).
- Los **asistentes reales** de Live Sessions se cargan a mano en la app (Firebase)
  y no están en el Sheet, por eso acá se compara inscriptos totales vs. activos.
