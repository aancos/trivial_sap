# Trivial SAP

Tarjetas tipo test sobre SAP (FI · MM · SD · HR) — sesión de 10 preguntas aleatorias con navegación adelante/atrás, racha, resultado final y exportación de tarjeta como imagen para LinkedIn.

Estética: fusión entre la barra de estado clásica de SAP GUI (cabecera de la tarjeta) y un cuerpo de tarjeta moderno estilo Fiori.

## Contenido
- `index.html` — app autocontenida (HTML + CSS + JS en un único archivo, sin dependencias de build). Solo carga fuentes de Google Fonts y `html2canvas` desde CDN.

## Publicar con GitHub Pages
1. Sube este archivo a la rama `main` del repo.
2. En GitHub → Settings → Pages → Source: rama `main`, carpeta `/ (root)`.
3. La app quedará disponible en `https://aancos.github.io/trivial_sap/`.

## Banco de preguntas
20 preguntas por módulo (80 en total), en `index.html`, dentro del array `QUESTIONS`. Para añadir más, sigue el mismo formato:

```js
{ module:"FI", q:"Pregunta...",
  options:["A","B","C","D"], correct:0,
  note:"Explicación breve." },
```

— Consultor en Sentido Común · aancos.com
