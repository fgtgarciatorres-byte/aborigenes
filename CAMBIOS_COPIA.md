# Copia con arreglos (27/10/2026)

Esta carpeta es una copia de `vida_aborigen_final`; el original no se ha tocado.

## Cambios (marcados `FIX (copia)`)
- **Botón de sonido (`game.js`)**: ahora activa un sonido ambiente real (viento suave generado con Web Audio, sin archivos nuevos). Arranca con el primer toque, sube y baja con fundido, se pausa si la pestaña se oculta y recuerda el estado en la partida guardada. `aria-pressed` ya no está invertido y el botón dice «Sonido ambiente: activado/silenciado» a los lectores de pantalla.
- **Textos pequeños (`styles.css`)**: ningún texto baja de 12 px (antes 10-11 px); el texto del rastreo con móvil horizontal pasa a 13 px; las etiquetas del mapa a 12 px mínimo.
- **`sw.js`**: caché `v9` para que los dispositivos que ya tenían el juego instalado descarguen los cambios.
- **`index.html`**: etiqueta y estado inicial del botón de sonido.
