# Trivial SAP

Tarjetas tipo test sobre SAP (FI · MM · SD · HR · BTP · BW · PM · QM · WM) — sesión de 10 preguntas aleatorias con navegación adelante/atrás, racha, resultado final y exportación de tarjeta como imagen para LinkedIn.

Las opciones de respuesta se barajan en cada sesión, así que la correcta no cae siempre en A o B.

Estética: fusión entre la barra de estado clásica de SAP GUI (cabecera de la tarjeta) y un cuerpo de tarjeta moderno estilo Fiori.

## Contenido
- `index.html` — app autocontenida (HTML + CSS + JS en un único archivo, sin dependencias de build). Solo carga fuentes de Google Fonts y `html2canvas` desde CDN.

## Publicar con GitHub Pages
1. Sube este archivo a la rama `main` del repo.
2. En GitHub → Settings → Pages → Source: rama `main`, carpeta `/ (root)`.
3. La app quedará disponible en `https://aancos.github.io/trivial_sap/`.

## Banco de preguntas
Dentro del array `QUESTIONS` en `index.html`:
- FI, MM, SD: 20 preguntas cada uno
- HR: 40 preguntas (las 20 originales + 20 de nivel avanzado: OM, nómina, retro, off-cycle, HCM P&F...)
- BTP, BW, PM, QM, WM: 20 preguntas cada uno

Total: 200 preguntas. Cada sesión sigue siendo de 10 preguntas aleatorias, aunque el banco del módulo elegido tenga 20 o 40.

Para añadir más, sigue el mismo formato:

```js
{ module:"FI", q:"Pregunta...",
  options:["A","B","C","D"], correct:0,
  note:"Explicación breve." },
```

El orden de las opciones se baraja automáticamente al arrancar cada sesión (`shuffleOptions`), así que no hace falta preocuparse por dónde coloques la respuesta correcta al escribir preguntas nuevas.

— Consultor en Sentido Común · aancos.com
