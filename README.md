# Trivial SAP

Tarjetas tipo test sobre SAP (FI · MM · SD · HR) — sesión de 10 preguntas aleatorias con navegación adelante/atrás, racha, resultado final, ranking global por módulo y exportación de tarjeta como imagen para LinkedIn.

Estética: fusión entre la barra de estado clásica de SAP GUI (cabecera de la tarjeta) y un cuerpo de tarjeta moderno estilo Fiori.

## Contenido
- `index.html` — app autocontenida (HTML + CSS + JS en un único archivo, sin dependencias de build). Solo carga fuentes de Google Fonts, `html2canvas` desde CDN, y llama al Worker del ranking.
- `worker.js` / `wrangler.toml` / `schema.sql` — backend del ranking: un Worker de Cloudflare con SQLite (D1) detrás. Se despliega aparte, no forma parte del sitio estático.
- `DEPLOY.md` — pasos para desplegar el ranking desde cero.

## Ranking global
Al terminar una sesión, cualquiera puede escribir su nombre y enviar su puntuación al ranking del módulo jugado (o "Todos"). La puntuación se calcula en el servidor como `aciertos × 1000 + bonus de rapidez (máx. 600 pts)`: los aciertos siempre pesan más que la velocidad. El ranking se lee desde cualquier punto de la app con el botón "🏆 Ver ranking".

Requiere haber desplegado el Worker una vez (ver `DEPLOY.md`) y haber sustituido el valor de `RANKING_API` en `index.html` por la URL real. Hasta entonces, la app funciona igual mostrando un aviso de que el ranking no está conectado.

## Publicar con GitHub Pages
1. Sube `index.html` (y este README) a la rama `main` del repo.
2. En GitHub → Settings → Pages → Source: rama `main`, carpeta `/ (root)`.
3. La app quedará disponible en `https://aancos.github.io/trivial_sap/`.

## Banco de preguntas
20 preguntas por módulo (80 en total), en `index.html`, dentro del array `QUESTIONS`. Para añadir más, sigue el mismo formato:

```js
{ module:"FI", q:"Pregunta...",
  options:["A","B","C","D"], correct:0,
  note:"Explicación breve." },
```

Si añades un módulo nuevo, recuerda darlo de alta también en `RANKING_MODULES` (índice.html) y en `MODULOS_VALIDOS` (worker.js) — si no, el ranking lo rechazará.

— Consultor en Sentido Común · aancos.com
