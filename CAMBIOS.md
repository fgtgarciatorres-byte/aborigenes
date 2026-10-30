# Vida Aborigen · Fase 8 (23/10/2026): tema de hoguera «Remedios y huesos que cuentan» (medicina)

El usuario aprobó todas las recomendaciones de `docs/MEDICINA.md` (§4); el detalle está en su §6. Se siguen las reglas de siempre:
- móvil y escritorio, sin conexión;
- 0 errores y 0 peticiones de red en las 5 resoluciones;
- no se han tocado los adjuntos;
- el código nuevo va marcado `// FIX (fase 8)`.

## Qué hay de nuevo
- **Tema «Remedios y huesos que cuentan»** en la pestaña «Temas de la noche».
  - Lo presenta **Fayna**.
  - Se desbloquea al preparar un remedio (cualquier receta médica) en «Fuego y cocina».
  - Muestra el **aviso médico** y una **nota de respeto**: los restos humanos son dibujos esquemáticos y no hay fotos de momias ni de cráneos.
- **⌕ Huesos que cuentan** (el juego principal): una mesa de estudio con lupa y cinco huesos.
  - Fémur 1740, soldado torcido.
  - Cráneo con un «golpe que se curó» en «luchas con reglas», sin armas ni cifras de muertes.
  - Caries en cueva frente a túmulo.
  - Líneas del esmalte.
  - Oído del mariscador.
  - Cada hueso da una ficha (+2), y el conjunto da la ficha «Cuidar se ve en los huesos» (+12).
  - Las opciones no salen siempre en el mismo orden.
- **Trepanación:** al terminar «Huesos que cuentan», la tarjeta pendiente pasa a «Desbloqueada · otra noche — Cráneos que se abrieron para curar». **No tiene juego** (no se pidió).
- **▥ La férula de Guayadeque:** se ordenan cinco pasos y la férula se dibuja por capas.
  - Etiquetas: arqueología de 1900, hipótesis (el orden) y no verificado (si la pieza se conserva hoy).
  - Lleva un aviso propio: «Hoy un hueso roto lo inmoviliza el personal sanitario».
  - Da +8 y la ficha «ferula».
- **✎ ¿Qué cuenta la crónica?:** seis casos.
  - En cada uno se elige lo que cuenta la fuente y si el dato es de Gran Canaria o de **otra isla**, y se ve «¿Y hoy?».
  - Las trampas son la borraja, las aguas de los balnearios, la tabaiba y el drago.
  - Al final hay un mapa: solo 2 de los 6 datos son de Gran Canaria.
  - Da +8 y la ficha «El mapa de los remedios».
- **❦ Herbario de Fayna:** solo fichas del Cuaderno, **sin recetas**. Tiene 10 cartas.
  - Tabaiba y cardón: ⚠ peligro, tóxicos.
  - Borraja y aguas de Firgas, Teror y Azuaje: folclore moderno.
  - Mocán y almácigo: otra isla.
  - El herbario también se abre desde el Cuaderno.
- **Fichas corregidas** (MEDICINA §2.2):
  - drago: madera de escudos, y el uso medicinal se documenta más tarde;
  - arrope: Abreu lo da «como medicina» para cámaras y dolor de costado en Tenerife; en Gran Canaria solo era comida;
  - cura con junco y manteca, con todos los detalles de Abreu y el 112;
  - paso del polvo de drago: «Molerla (así la vendían los boticarios)».
- **Fuentes nuevas** en `SRC`. Chil y Naranjo (1900) sigue marcado **[NO VERIFICADO]**.
- **Arte nuevo** sin texto: `img/medicina/cueva_remedios.webp`, `mesa_estudio.webp` y `ferula_materiales.webp`. Los huesos, la férula y el mapa de islas son SVG.

## Técnico
- `game.js`:
  - bloque nuevo al final, antes de `#rotateContinue`;
  - `migrate()` llama a `migrateF8()`, que repara `state.night.med`;
  - `fireTopics()` muestra las historias anunciadas (`teaser`);
  - `listenTale()` muestra `h.warning`;
  - `showJournal()` tiene el botón «Herbario de Fayna».
- `styles.css`: bloque «FIX (fase 8)».
  - Botones de 44 px o más.
  - Pulso de la lupa, desactivado con movimiento reducido.
  - Rejilla del herbario y reglas para horizontal bajo.
- `sw.js`: caché **v8**, con las 3 imágenes nuevas.

## Pruebas
- `pruebas_va/run_fase8.js` en 1280×800 y 1920×1080 con ratón, y en 360×640, 390×844 y 844×390 táctil.
  - Recorre: tema bloqueado → remedio → tema; los 5 huesos con un fallo; la historia anunciada; la férula con un error; los 6 casos con una isla equivocada; las 10 cartas del herbario; el herbario desde el Cuaderno; las fichas corregidas.
  - Resultado: **0 errores, 0 peticiones de red**, sin desbordamiento y sin botones táctiles de menos de 44 px. En escritorio con ratón solo aparecen los botones de cabecera que ya había.
- `pruebas_va/migra8_test.js`: partidas sin `night`, de la fase 7b, con `med` a medias, corrupto o basura. Todas cargan y los juegos abren. Sin remedio, el tema sigue cerrado.
- Regresión: `run_fase7.js` y `run_fase7b.js` en las 5 resoluciones, `migra_test`, `migra6`, `migra7` y `migra7b` dan 0 errores y 0 red. `sw_test.js` da caché v8 (196 archivos) y funciona sin conexión.
- Capturas en `capturas/fase8/`.

# Vida Aborigen · Fase 7b (22/10/2026): arqueoastronomía en «Lunas y estrellas»

Diseño aprobado por el usuario (ver `docs/ARQUEOASTRONOMIA.md`, §3 y §6). Todo va dentro del tema de la hoguera **«Lunas y estrellas»**; se mantienen «Mirar el cielo» y «La rueda del año».

Mismas reglas de siempre:
- Móvil y escritorio, sin conexión, 0 errores de consola y 0 peticiones de red (probado en 1280×800, 1920×1080, 390×844, 844×390 y 360×640 táctil).
- No se han tocado los adjuntos ni las imágenes que ya había. Las 5 imágenes nuevas (`img/noche/pared_horizonte.webp`, `pared_roca.webp`, `bentayga.webp`, `cuatro_puertas.webp`, `cumbres_noche.webp`) son WebP 1280×720 sin texto ni personas.
- Los cambios de código llevan `// FIX (fase 7b)`. El módulo nuevo va en un bloque de `game.js` justo después de `skyCalendar()`; las fuentes nuevas (`SRC`), justo después de las de Risco Caído.
- Cada dato lleva etiqueta: **Medido en el yacimiento** (nueva, verde agua), dato astronómico, crónica, hipótesis o deducción del juego.

## Juegos nuevos (botones del tema «Lunas y estrellas»)

### ☾ La pared de las lunas
- Una cueva **imaginada** (inspirada en cuevas reales de Gran Canaria; el juego lo dice en el aviso inferior) que mira al este. Sale la luna llena: el jugador toca el horizonte donde ha salido (o mueve la marca con ◀ ▶ y pulsa «Marcar aquí», ±5° de margen). A la mañana siguiente marca el sol. Cada luna se graba en «Tu pared» y en la «tara» (tabla de rayas).
- 13 lunas llenas reales, del 7-7-1447 al 25-6-1448, calculadas para 28° N (horizonte llano). Acimuts de la luna de 58° a 123° y del sol de 63° a 116°.
- **Dos modos**: «Una luna cada noche» (una luna por visita a la hoguera; el contador `night.nights` sube cada vez que se entra desde el mapa y se guarda) y «Todas seguidas».
- Preguntas cortas en las lunas 4, 7, 10 y 13. +2 de saber por luna y por pregunta.
- **Lee tu pared**: la pared con guías (solsticios, equinoccio, extremos de la luna), lista de lo que se ve, 3 preguntas (+3 cada una, +10 al final), una línea de 13 lunas con las dos versiones de las crónicas (año que empieza en primavera / fiestas a fines de junio) y el **debate abierto**: «¿para qué servían estas marcas de luz?» (calendario / lugar sagrado / las dos cosas / no se puede saber), con ICOMOS 2019 y Caballero y Esteban 2023. Elegir opinión da +2 la primera vez; ninguna respuesta es «la buena».
- Ficha nueva: **la tara**; ficha **debate**.

### La luna del Roque Nublo (se abre desde «Lee tu pared»)
- Desde el Bentayga, mover los años 1438–1456 hasta que la luna llena del verano salga justo tras el Roque Nublo (parada mayor, ciclo de 18,6 años).
- Texto [MEDIDO]: IAC y Gil y Belmonte (2009), 9-7-2006, última parada mayor 2024-2025, próxima 2043. Aviso visible: **«Esto se ha medido; no sabemos si lo buscaban.»** Ficha nueva **lunasticio**, +6.

### ◬ El ojo del Bentayga
- Vista desde la cazoleta del almogarén: el sol de media mañana pasa por la muesca en V (acimut 101,8°) y una cuña de luz cae sobre el suelo. Días del 10-9 al 30-9 y del 10-3 al 31-3. Encaja hacia el 22-23 de septiembre (y en torno al 20-21 de marzo, con la nota de Esteban sobre la precisión).
- «Un paso» a izquierda o derecha: el sol deja de verse en la muesca, aunque la mancha de luz no cambia; **el sitio para mirar es la cazoleta** (+3).
- Ficha **bentayga**, +8. Etiquetas: medido (efecto de luz) e hipótesis (uso como calendario).

### ☀ El día más largo en Cuatro Puertas
- Plano visto desde arriba (esquema, no a escala) de la cueva de cuatro bocas abierta al norte. Deslizador del 1 de mayo al 31 de agosto, amanecer o atardecer.
- Solo cuando la declinación del sol pasa de 23,0° (unos días alrededor del 21 de junio) entra la luz: al amanecer por la puerta 2; al atardecer por las puertas 3 y 4, hasta la cazoleta de la esquina sureste.
- Ficha **cuatropuertas**, +8, y botón a la ficha **La Angostura** (solsticio de invierno, solo ficha).

## Correcciones de contenido

- **Risco Caído**: la etiqueta pasa a «Efecto de luz medido · uso como calendario: hipótesis discutida». Ficha y esquema hablan de **dos puntos de luz** que llegan hacia el 19 de marzo y se juntan en una imagen cerca del equinoccio (dejan de llegar hacia el 25 de septiembre). Aviso de ICOMOS (2019) y petición de publicaciones técnicas de Caballero y Esteban (2023).
- Referencia de Risco Caído completada: Cuenca Sanabria et al. (2018), *Mediterranean Archaeology and Archaeometry* 18(4), 11-18, DOI 10.5281/zenodo.1472250.
- Ficha **lunas**: Torriani («520 esplendores de la luna», es decir, lunas llenas) y Sedeño («acabada la sementera, por fines de junio»): las dos crónicas coinciden en junio para la cosecha y la fiesta.
- **La rueda del año**: nueva etiqueta «Medido en el yacimiento». Marzo y septiembre: Risco Caído y Bentayga. Junio: Cuatro Puertas. Julio: parada mayor de la luna y Roque Nublo (ciclo de 18,6 años). Diciembre: La Angostura. **Abril**: se quita «Las Pléyades también se ocultan» (no estaba bien respaldado).
- El tema de la hoguera añade una línea: «hacían rayas para no olvidar la cuenta… para qué lo usaban, eso todavía lo discuten los sabios».

## Técnica

- `migrateF7b()` (llamada desde `migrate()`): crea `night.nights`, `night.wall`, `night.bentayga` y `night.cuatro` sin tocar lo anterior; repara valores corruptos (luna fuera de rango, modo desconocido, etc.).
- `sw.js`: caché **v7** con las 5 imágenes nuevas (193 archivos).
- CSS nuevo al final de `styles.css`: escritorio ≥1100 px con escenario y panel lateral; horizontal bajo (≤500 px de alto) con el escenario fijo a la vista mientras se lee el panel; vertical apilado; botones de 44 px o más; `prefers-reduced-motion` desactiva las animaciones de salida.
- Las pantallas usan `activity-screen astro-screen` (no `mini-screen`): no salta el aviso «Gira el móvil».

## Pruebas

- `pruebas_va/run_fase7b.js` (5 resoluciones): juega la pared en los dos modos (incluido salir al mapa y volver para otra noche), 13 lunas, lectura, debate, Roque Nublo, Bentayga (encaje y «un paso»), Cuatro Puertas (amanecer y atardecer), rueda del año y Risco Caído. Resultado: 0 errores, 0 peticiones, 6 fichas nuevas en el cuaderno, sin desbordamiento ni botones táctiles de menos de 44 px.
- `pruebas_va/migra7b_test.js`: partidas de la fase 6, de la fase 7, con pared a medias y con datos corruptos; contador de noches tras recargar.
- Regresión `run_fase7.js` (5 resoluciones) y `migra6/migra7_test.js`: sin cambios. `sw_test.js`: caché v7 sin conexión.
- **Capturas:** `capturas/fase7b/` (01–20 por resolución). No van dentro del zip.

# Vida Aborigen · Fase 7 (22/10/2026): la noche · historias en la hoguera y astronomía

Mismas reglas de siempre:
- Funciona en móvil y en escritorio, sin conexión, con 0 errores y 0 peticiones de red.
- Las 2 imágenes nuevas (`img/noche/hoguera.webp` e `img/noche/cielo.webp`) son WebP sin texto ni personas. La casa tiene azotea plana de piedra, sin techo de paja.
- No se han tocado los adjuntos ni las imágenes que ya había.
- Los cambios de código llevan `// FIX (fase 7)` (o `/* FIX (fase 7) … */`). Todo el módulo nuevo va en un bloque de `game.js`, justo después de `migrateF6()`.
- Lo dudoso lleva una etiqueta (crónica, hipótesis, deducción, leyenda moderna, otra isla) y su fuente.

## Decisión de diseño: la hoguera es el centro de los temas

- En el mapa hay un botón nuevo, **«🔥 La hoguera · historias de la noche»**. Lleva a una escena nocturna con tres pestañas:
  - **Tu historia**: los recuerdos del jugador.
  - **Cuentos y leyendas**.
  - **Temas de la noche**: cada tema empieza como una historia junto al fuego y desde ella se abre su juego.
- Todo sale de **un único registro**, `HEARTH`, que se rellena con `registerHearth({...})`. La interfaz no tiene listas fijas: si se registra algo nuevo, aparece solo en la pestaña que le toca.
- Los temas futuros (medicina, trepanación, momias, pastoreo, conflictos entre guanartematos y razias de esclavos) **no se han construido**.
  - Están registrados con `pending: true` y salen como 6 tarjetas anónimas: «Historia por descubrir · Alguien junto al fuego guarda esta historia para otra noche».
  - No muestran título, tema ni pista, así que no hay spoilers. La prueba comprueba que su texto no menciona ningún tema.

## A · Tu historia (recuerdos → relato)

- Cada experiencia superada en la partida desbloquea un **recuerdo**. Hay 15:

| Recuerdo | Se desbloquea con |
|---|---|
| El salto del pastor | superar el salto con garrote (`done.salto2`) |
| Huellas en el barro | cualquier nivel del rastreo de animales |
| Las támaras de la palmera | el reto de las támaras |
| El molino y el gofio | fabricar el molino de mano o el gofio |
| Sembrar y cosechar | la cosecha o empezar el ciclo de los campos |
| El granero colectivo | guardar grano en el granero |
| Cocinar para todos | cualquier comida de «Fuego y cocina» |
| Marisqueo en la costa | el marisqueo en los charcos |
| Pescar en la orilla | pescar la vieja |
| Manos en el taller | cuero, estera, bolsa, anzuelo o garrote |
| Moler colores | cualquier pigmento |
| Pintar triángulos | una obra en el juego de pintado (o el friso) |
| Pedir la lluvia | el rito de la lluvia del almogarén |
| Ecos de La Gomera | el silbo |
| Mirar el cielo | completar el minijuego del cielo |

- Los recuerdos que aún no tienes salen bloqueados, con una pista de cómo conseguirlos.
- **Cómo se cuenta la historia:**
  - Eliges de 2 a 4 recuerdos **en el orden** en que quieras contarlos. El número de cada uno se ve en una insignia; si vuelves a tocar un recuerdo, se quita.
  - Pulsas «Contar junto al fuego».
- **El relato**, en español:
  - empieza con una frase de apertura;
  - sigue con un fragmento por recuerdo, unidos con conectores («Primero…», «Después…», «Más tarde…», «Al final…»);
  - termina con un cierre según la mezcla de temas (risco, campo, mar, taller, saber).
- **Reacciones:** responden dos oyentes, cada uno según el recuerdo que le toca (Idaira, Fayna, Nauzet o Guayarmina), y cierra Areguía. Se muestran sus retratos.
- **¿Qué es dato y qué es relato?** Debajo de cada relato, un recuadro explica que el relato añade detalles y emociones. Enlaza las fichas con fuente de los recuerdos usados.
- **Saber:** +6 por la primera historia y +4 por cada combinación u orden nuevo (hasta 8 premios). Repetir la misma combinación no da puntos. Las historias se guardan en `state.night.told`.

## B · Cuentos y leyendas (etiquetados)

| Cuento | Etiqueta | Se desbloquea con |
|---|---|---|
| Nos pusieron aquí y nos olvidaron | Relato recogido por un cronista (Bernáldez) · Gran Canaria | desde el principio |
| Atidamana y Gumidafe | Crónica · entre historia y leyenda (Abreu Galindo); abre también la ficha «¿Quién decidía?» | desde el principio |
| Los tibicenas | Creencia recogida por un cronista · Gran Canaria (y se avisa de la mirada cristiana del fraile) | rastrear al perro |
| Gente de tierra y agua | **Otra isla: Tenerife** · crónica | contar tu primera historia |
| Gara y Jonay | **Leyenda moderna · La Gomera (s. XIX)**: no es aborigen | probar el silbo |

- Cada cuento se escucha en una ventana con la voz de un personaje y su reacción.
- La ficha del cuento pasa al Cuaderno. Escucharlo por primera vez da +3 de saber.

## C · Tema «Lunas y estrellas» (astronomía)

- Se desbloquea al visitar el almogarén o al contar la primera historia. Lo narra Idaira (las lunas según Abreu Galindo y Marín de Cubas, que no coinciden).
- Desde el tema se abren dos juegos.
- **Mirar el cielo** (escena `cielo`, SVG 1600×900 sobre una silueta de cumbres):
  - Es una noche de invierno mirando al sur.
  - Hay que encontrar, en orden, las **Pléyades**, las **3 estrellas del cinturón de Orión**, **Sirio** y **Canopo**. Hay estrellas de relleno.
  - Se toca o se pulsa la estrella; el acierto se calcula por cercanía, con un margen generoso en el móvil. También funciona con el teclado.
  - Tiene botón **Pista**. Si tocas otra estrella antes de tiempo, el juego te lo dice.
  - Cada estrella abre su ficha: lo astronómico, lo que dicen las fuentes y lo que **no** se sabe.
  - Saber: +5 por estrella y +5 por terminar.
- **La rueda del año**:
  - Es un círculo de 12 meses con las fases de la luna en el centro. Se toca un mes en la rueda o en la cuadrícula.
  - Cada dato del mes lleva su tipo (**Dato astronómico, Crónica, Hipótesis, Deducción del juego**) y un enlace [fuente].
  - Une el cielo con el calendario agrícola de la fase 6 (lluvias, siembra, siega, granero) y con el almogarén (rito de la lluvia y luz de **Risco Caído**, siempre como hipótesis).
  - Tiene botones a «Ver la luz de Risco Caído», «Ritos de la lluvia», «Mirar el cielo» y «Volver a la hoguera».
- Las estrellas se llaman con sus **nombres de hoy**, y así se dice en pantalla. No se inventa ningún nombre aborigen de estrellas ni de constelaciones.

## Cómo registrar un tema nuevo

1. Escribe su juego como una función normal que pinte una pantalla con `go(html, clase, escena)`, por ejemplo `function momiasGame() {…}`. Si necesita estado, guárdalo en `state` y añade los valores por defecto en una `migrateF8()`, igual que `migrateF7()`.
2. Añade las fichas con fuente a `fichas` (y las fuentes nuevas a `SRC`).
3. Regístralo después del bloque de la fase 7 (o en lugar de su marcador `pending`; si el `id` es el mismo, `registerHearth` lo **sustituye**):

```js
registerHearth({
  kind: 'tema',                 // 'recuerdo' | 'cuento' | 'tema'
  id: 'momias',                 // único; si coincide con uno «pending», lo reemplaza
  title: 'Los que se quedaron',
  label: 'Arqueología · El Museo Canario',   // etiqueta visible (si falta, se usa la de la ficha)
  ficha: 'momias',              // ficha del Cuaderno que se añade al escucharla
  unlock: s => !!s.done.templo, // condición sobre el estado; sin unlock = abierto
  hint: 'Visita el almogarén.', // pista mientras está bloqueado
  hook: 'Areguía baja la voz: «En las cuevas de los barrancos…»',  // gancho sin spoilers para la tarjeta
  npc: 'Areguía',               // quién la cuenta (Idaira, Fayna, Nauzet, Guayarmina, Areguía)
  react: 'Hay que mirar con respeto.',       // frase final del narrador
  body: ['Párrafo 1…', 'Párrafo 2…'],        // la historia junto al fuego
  games: [{ id: 'momiasBtn', label: '◇ Entrar en la cueva', open: () => momiasGame() }]  // opcional: botones que abren el juego
});
```

- Para que un tema salga como «Historia por descubrir» sin dar pistas: `registerHearth({ kind: 'tema', id: 'momias', pending: true })`.
- Para añadir un **recuerdo** nuevo cuando exista un juego: `kind: 'recuerdo'` con `icon`, `cat` ('risco' | 'campo' | 'mar' | 'taller' | 'saber'), `unlock`, `hint`, `npc`, `react`, `ficha` y `frag: () => 'texto en primera persona, en pasado'`.
- Para un **cuento**: `kind: 'cuento'` con `title`, `hook`, `ficha` (con su etiqueta: crónica, leyenda, otra isla…), `npc`, `react` y `unlock`.
- Si el juego añade imágenes, súbelas a `sw.js` (cambia la versión de la caché) y añade su escena a `SCENES`.

## Partidas guardadas

- `migrateF7()` (la llama `migrate()`) añade `state.night = { told: [], heard: {}, sky: {}, stories: 0 }`. Si la partida ya tenía una parte, completa lo que falta.
- Lo anterior se conserva: saber, bolsillo, galería, rastreo, campos y granero.

## Descartado (y por qué)

- **Nombres aborígenes de estrellas** (por ejemplo, «Chaxiraxi = Canopo» o nombres guanches para Orión o las Pléyades): no hay fuente fiable. Se usan los nombres de hoy.
- **Constelaciones aborígenes inventadas:** no hay ninguna.
- **«El Bentayga marca los equinoccios» y otras alineaciones sin estudio publicado:** no salen. La única luz que se muestra es la de **Risco Caído**, como hipótesis.
- **Pléyades y Sirio como cultos de Gran Canaria:** no hay datos de esta isla. Las Pléyades salen con la hipótesis de Tindaya (Fuerteventura) y Sirio solo como dato astronómico.
- **«Beñesmer» como fiesta de Gran Canaria:** el nombre es de Tenerife. Se cita solo dentro de la hipótesis de Barrios.
- **Supuesta inscripción del Bentayga de webs divulgativas:** sin respaldo.
- **Gara y Jonay como mito aborigen:** sale, pero como leyenda moderna de La Gomera.
- **Medicina, trepanación, momias, pastoreo, guanartematos y razias:** se dejan para fases futuras, como se pidió.

## Datos sin confirmar (y cómo se presentan)

- **Calendario de Risco Caído:** hipótesis.
- **Canopo y las fiestas de agosto:** hipótesis discutida (Barrios).
- **Pléyades como «nubecitas» de los antepasados:** hipótesis de otra isla.
- **Inicio del año:** «acano» y la luna nueva tras el solsticio vienen de Marín de Cubas; Sedeño habla de la primavera. Se muestran las dos versiones.
- **Atidamana:** el cronista escribe más de un siglo después y los nombres varían.
- **Mes de siembra y tareas del campo:** deducción del juego.
- **Fechas de aparición de las estrellas:** valen para los siglos XI-XV y son aproximadas. El cielo es un esquema simplificado.

## Pruebas (cierre de la fase 7)

- **`pruebas_va/run_fase7.js`** carga una partida avanzada de la fase 6, sin `night`, y vuelve al mapa con `?volver=mapa`. Recorre:
  - la migración;
  - los recuerdos: 12 abiertos y 3 bloqueados;
  - elegir 4 recuerdos en orden y contar la historia (6 párrafos, 3 voces, 4 fichas de dato, +10 de saber);
  - repetir la misma historia, que no da puntos;
  - los cuentos con sus etiquetas, escuchando Gara y Jonay, Atidamana y Tierra y agua;
  - los temas: «Lunas y estrellas» más 6 tarjetas por descubrir sin spoilers;
  - el cielo: un toque equivocado, la pista y las 6 estrellas tocadas en pantalla (4 pasos);
  - la rueda del año (agosto y junio);
  - la vuelta a la hoguera, con el recuerdo «Mirar el cielo» ya desbloqueado;
  - el Cuaderno (8 fichas nuevas) y el guardado.
- **Resultado:** 1280×800 y 1920×1080 con ratón; 390×844, 844×390 y 360×640 con pantalla táctil. En las cinco: recorrido completo, 0 errores de consola y 0 peticiones de red. En el móvil, ninguna de las 13 pantallas auditadas tiene desbordamiento horizontal, botones de menos de 44 px ni elementos fuera de la pantalla.
- **Migración** (`migra7_test.js`): una partida de la fase 6 sin `night` y otra con `night` incompleto cargan bien. Conservan todo y la hoguera funciona.
- **Regresión:** `run_fase6.js` (las 5 resoluciones), `migra6_test.js` y `migra_test.js`.
- **Sin conexión** (`sw_test.js`): la caché es ahora `vida-aborigen-v6` e incluye las 2 imágenes nuevas.
- **Corregido durante las pruebas:**
  - un cambio de nombre (`has` → `hasMade`) había roto el `Set` de símbolos encontrados;
  - la pista del cielo se leía rara;
  - en el móvil, al cambiar de pestaña, el contenido quedaba fuera de la vista.
- **Capturas:** `capturas/fase7/` (01–13 por resolución). No van dentro del zip.

## Limitaciones

- Los relatos se construyen con fragmentos fijos más conectores: son variados, pero no infinitos.
- El cielo es un esquema: no gira con la hora ni con la fecha.
- Las fichas de astronomía resumen fuentes en español y en inglés de forma sencilla para 1.º y 2.º de ESO. Si se quiere usar la hipótesis de Barrios en clase, conviene leer el artículo.
- Pruebas emuladas: conviene probarlo una vez en un móvil Android y en un iPhone de verdad.

# Vida Aborigen · Fase 6 (22/10/2026): monte, rastreo de animales, agricultura y cocina unificada

Mismas reglas de siempre:
- Funciona en móvil y en escritorio, sin conexión, con 0 errores y 0 peticiones de red.
- Las imágenes nuevas son WebP sin texto incrustado, con flora y fauna nativas solamente (sin tuneras, pitas ni saguaros).
- No se han tocado los adjuntos ni las imágenes que ya había en `img/`: solo se añaden 30 archivos nuevos en `img/bosque/`, `img/campos/`, `img/fauna/` e `img/iconos/`.
- Los cambios de código llevan `// FIX (fase 6)` (o `/* FIX (fase 6) … */` dentro de las funciones de una línea).
- Cada dato lleva su fuente en la ficha o en la leyenda, y lo dudoso va marcado como tal.

## A · Recolección en el monte

- **Sustituye** al antiguo modal «Recolectar» (no hay duplicado). Es una escena explorable con tres zonas: **laurisilva**, **pinar** (fondo nuevo) y **palmeral y barranco**.
- Lo que se puede recoger **brilla**. Al tocarlo aparece una leyenda breve con el nombre científico, la temporada, el aviso de protección y las fuentes. Al recogerlo, el fruto **vuela al zurrón**.
- **Recursos:** mocán, madroño canario, bicácaro, hojas de laurel, madera caída, junco, piñones de pino canario, tea, dátiles, hojas de palma, resina de drago, piedras y miel silvestre.
- **Solo se observan:**
  - El helecho: la harina de su raíz está documentada en El Hierro, La Palma y Tenerife, pero **no en Gran Canaria**.
  - La jara de pinar.
- **Estaciones** (`state.time`; empieza en otoño): los frutos solo están disponibles en su temporada, que es **orientativa** (fenología actual). El resto se recoge una vez por partida, como antes.
- **Aviso de protección**: la Orden de flora de 1991 pone en su anexo II al mocán, el madroño, el bicácaro y la palmera, y el pino canario va en el anexo III. Se añade el mensaje «nunca se arranca una planta de raíz» y la ficha «Proteger el monte hoy».

## B · Rastreo de animales

- El rastreo de la cabra de la Jornada 1 es el **nivel 1**: no se repite.
- Desde el Rebaño se abre «Rastreo de animales», con 9 niveles que se desbloquean en orden. Cada nivel tiene tres pasos:
  1. **Deducir** el animal a partir de tres señales, con 2 a 5 opciones según el nivel.
  2. **Seguir el rastro** en 3 tramos: hay que examinar cada señal y decidir si es la buena, entre 1 y 3 distractores de animales parecidos.
  3. **Encontrar** al animal, que se muestra con su ficha y sus fuentes.
- **Animales:** oveja de pelo, perro aborigen, cerdo, lagarto gigante (*Gallotia stehlini*), cuervo, paloma bravía, pinzón azul, guirre y guaniles.
- **Curiosidad:** los huesos de la rata gigante (*Canariomys tamarani*), con su datación discutida.
- **Fuera:** el conejo y las perdices, porque llegaron con la conquista o después (lo explica una ficha).
- **Señales** dibujadas en SVG: huellas, excrementos, pelos y cerdas, plumas, ramoneo, hozaduras, egagrópila, piña picoteada, restos de carroña y sonidos. Son esquemas **simplificados**, y así lo dice el juego.

## C · Agricultura y almogarén

- **«Campos de cultivo»** (antes «Campos de cebada») recorre el ciclo completo en 6 pasos:
  1. Elegir **semilla sana**: se descartan la de gorgojo, la de moho y la germinada.
  2. **Sembrar** con el palo cavador, solo en otoño o invierno (una **deducción**), y abrir la **acequia** (Abreu).
  3. **Cuidar** el campo (malas hierbas y pájaros) dejando pasar las estaciones.
  4. **Cosechar** en primavera o verano, con los **higos** en verano.
  5. **Trillar** (Abreu) y **aventar** (una **reconstrucción**).
  6. **Granero**: un silo colectivo como Valerón o Risco Pintado, con laurel contra el gorgojo y la boca sellada con losa y barro.
- **Cultivos:** solo los de la arqueobotánica de Gran Canaria: cebada, trigo, lentejas, habas, guisantes e higos.
- **Sin duplicados:** el Almacén sigue siendo el mismo, ahora con la «cebada de la reserva» (para que el encargo del gofio no dependa del ciclo) y el estado del granero colectivo.
- **Almogarén · Ritos de lluvia y calendario:**
  - Ordenar el rito de la sequía según Abreu (Tirma y Umiaya, harimaguadas, leche y manteca, varas en el mar), con el aviso de que es la versión de un cronista.
  - Un esquema de la **cueva 6 de Risco Caído** con un deslizador de meses. Es una **hipótesis** de calendario lunisolar (UNESCO 2019, IAU).

## D · Cocina unificada

- La estación «Medicinas y comida» pasa a llamarse **«Fuego y cocina»** (mismo id; no se duplica). Tiene tres grupos: el fuego, las comidas por **origen** (campo, ganado, mar, monte) y los remedios de las crónicas con su aviso.
- **Recetas nuevas:** gofio amasado, frangollo de trigo, carne asada, potaje de legumbres (**reconstrucción**), higos pasados, y piñones con dátiles.
- **Ingredientes nuevos:** el Rebaño da ahora **leche** (×2) y **carne**.
- **Queso:** no hay. Sedeño dice que en Gran Canaria «el uso y arte de quesear no lo conocieron».
- **Ficha de la dieta:** una tabla por origen, con fuentes, que marca lo que ya has conseguido. Lo que no es de la época sale tachado.

## Partidas guardadas

- `migrateF6()` añade `time`, `forest`, `tracks`, `farm` y `granary` a las partidas antiguas.
- Se conserva lo ya recogido (`gathered`), el bolsillo, la galería, los símbolos y todo lo fabricado.
- Una partida que ya hubiera segado la cebada de los antiguos Campos ya no puede volver a tomar la cebada de la reserva del Almacén, porque usan la misma marca. Así no se duplica.

## Descartado (y por qué)

- **Raíz de helecho como alimento:** documentada en El Hierro, La Palma y Tenerife, no en Gran Canaria. Solo se observa.
- **Jara de pinar:** no consta su uso aborigen. Solo se observa.
- **Conejo y perdices:** llegaron con la conquista o después. Salen tachados en la ficha de la dieta y tienen su ficha propia.
- **Queso:** Sedeño dice que en Gran Canaria no se conocía. Sale tachado.
- **Cultivos sin respaldo arqueobotánico en Gran Canaria:** no aparecen. Solo están cebada, trigo, lentejas, habas, guisantes e higos.

## Datos sin confirmar (y cómo se presentan)

- **Temporadas de los frutos:** son orientativas y salen de la fenología actual.
- **Mes de siembra (otoño o invierno):** es una deducción.
- **Aventado y potaje de legumbres:** son reconstrucciones.
- **Miel silvestre:** viene de una sola fuente escrita, y su temporada es una suposición.
- **Calendario de Risco Caído:** es una hipótesis (calendario lunisolar).
- **Rito de la lluvia:** es la versión de un cronista (Abreu Galindo).
- **Rata gigante (*Canariomys tamarani*):** la datación de sus restos y su relación con la población humana están discutidas.
- **Señales del rastreo:** son esquemas simplificados, no calcos de huellas reales.

## Pruebas (cierre de la fase 6)

- **Regresión completa:** `pruebas_va/run_fase6.js` amplía la de la fase 5. Va de la portada al final y pasa por:
  - la jornada 1, el mapa, el pueblo, los retos y el almogarén con Balos;
  - los ritos y el calendario, el monte (tres zonas y el cambio de estación) y el ciclo agrícola completo;
  - el almacén, la cantera, el rebaño y los 9 niveles del rastreo con la curiosidad;
  - las 4 estaciones con las 6 recetas nuevas y la ficha de la dieta, el molino y el bolsillo;
  - el marisqueo y la pesca, los pigmentos, el pintado (27 símbolos, pared, vasija, PNG, galería y reto);
  - el salto y las támaras, el cuaderno, el silbo, el final, y una recarga que lo conserva todo.
- **Resultado:** 1280×800 y 1920×1080 con ratón; 390×844, 844×390 y 360×640 con emulación táctil. En las cinco: recorrido completo, 0 errores o avisos de consola y 0 peticiones de red. En móvil, en las 64 o 65 pantallas auditadas no hay desbordamiento horizontal ni botones de menos de 44 px.
- **360×640:** la pasada anterior se cortó a mitad del rastreo porque se interrumpió el trabajo, no por un fallo del juego. Se ha repetido entera y sale limpia.
- **Migración** (`migra6_test.js`): una partida de la fase 5 con bolsillo, galería, símbolos, gofio y vasija decorada carga sin errores. Recibe `time`, `forest`, `tracks`, `farm` y `granary`, y lo anterior se conserva.
- **Sin conexión** (`sw_test.js`, servido por http local): la caché `vida-aborigen-v5` (antes v4) guarda 186 entradas, que son todos los archivos del juego y del silbo, incluidas las 30 imágenes nuevas. No falta ninguna ni sobra ninguna inexistente. Con la red cortada vuelven a abrirse el juego y el silbo.
- **Corregido durante el cierre:** el título del rastreo decía «Sigue a pinzón azul…». Ahora lleva el artículo correcto: «Sigue al pinzón azul», «a la oveja de pelo», «a los guaniles», y también en «la que deja…». Se hace con `faunaArt()`. Tras el cambio se han repetido las cinco resoluciones, que salen limpias.
- **Capturas:** están en `capturas/fase6/` (A1–A7, B0–B6, C1–C9 y D1–D4 por resolución, más la regresión 01–52). No van dentro del zip.

## Limitaciones

- El sonido del silbo no se ha probado en un iPhone real. Chrome headless no reproduce audio.
- El monte, los campos, el rastreo, el marisqueo, el pintado y los retos del risco se ven mejor en apaisado. En vertical sale el aviso de girar, aunque se puede seguir jugando.
- En escritorio algunos botones de la barra superior miden menos de 44 px (32–39 px). Ahí se usa el ratón, y el criterio de 44 px se aplica al móvil.
- La estación avanza solo con «Dejar pasar la estación», que está en el monte y en los campos. No hay un calendario automático.
- Las pruebas son emuladas (Chrome con pantalla táctil). Conviene probarlo al menos una vez en un móvil Android y en un iPhone de verdad.

# Vida Aborigen · Fase 5 (22/10/2026): juego de pintado (símbolos, colorantes y composición)

Mismas reglas que en las fases anteriores:
- Funciona en móvil y en escritorio, sin conexión, con 0 errores de consola y 0 peticiones de red.
- Ninguna imagen lleva texto incrustado. Los símbolos son **dibujos SVG nuevos**, hechos a mano en el código (no son fotos ni calcos de fotos con derechos).
- No se han tocado los adjuntos originales ni las imágenes que ya había en `img/`. Esta fase no añade imágenes.

Los cambios de código llevan `// FIX (fase 5)` (o `/* FIX (fase 5) … */` dentro de las funciones de una línea).

## 1. Qué sustituye

Antes había tres recetas de decoración: «Panel geométrico», «Vasija decorada» y «Cuero estampado», con un minijuego de sellos.
- Las tres se han quitado y su lugar lo ocupa **un único juego de pintado**, en la estación de Pigmentos. No hay duplicados.
- El **cuero** desaparece como soporte, porque no hay pruebas de que las pintaderas se usaran para estampar cuero. Sus motivos pasan a ser símbolos de pintadera.
- La ficha `pintaderas` ya no habla de cuero ni de «sellos de propiedad» como si fueran hechos: se presentan como hipótesis.

## 2. El juego en tres pasos

**Paso 1 · Elegir símbolos.**
- Hay 27 motivos documentados. Al empezar tienes 3; los demás se **descubren** en cinco lugares (ver tabla).
- Cada motivo tiene una mini ficha con su nombre, la isla y el yacimiento o tipo de objeto, la técnica original, una nota y las fuentes del grupo.
- Para pintar se eligen entre 1 y 8 motivos.

**Paso 2 · Hacer los colorantes.**
- Se usan las recetas de la fase 4: rojo de almagre, blanco de tierra clara y negro de hollín de tea.
- Solo se puede pintar con los colores que ya has preparado.
- Desde este paso se puede ir a preparar uno; al terminar, el botón «Volver al juego de pintado» te devuelve aquí.

**Paso 3 · Componer en un soporte.**
- **Pared de toba:** un paramento con textura, que es lo que se pintó en la Cueva Pintada.
- **Vasija de Gran Canaria:** una silueta con asas de mamelón y tres frisos marcados.
  - Al tocar, la figura se ajusta a la banda más cercana y se queda dentro del perfil de la vasija.
  - Este soporte gasta 1 cerámica y crea «Vasija decorada».
- **Herramientas:**
  - Poner una figura: toca el símbolo y después el soporte, o arrástralo desde la paleta.
  - Elegir una figura: tócala. Moverla: arrástrala.
  - Girar 45°, agrandar o reducir, «Repetir en friso» (rellena la fila) y «Friso alterno» (alterna con otro motivo o color, A-B-A-B).
  - Cambiar el color de la figura elegida, borrarla, deshacer (hasta 50 pasos) y «Borrar todo» (pide un segundo toque para confirmar).
  - Banda de color de fondo.
  - Teclado: flechas, R, + / − y Supr.
  - Bolsillo: un pigmento del bolsillo elige el color.
- **Guardar:** hacen falta 3 figuras como mínimo.
  - La obra va a la **galería local**: hasta 12 obras, en la clave `vida-aborigen-galeria-v1`, sin nombres ni fechas.
  - La galería no se borra al empezar una partida nueva.
  - Se puede **descargar en PNG** sin conexión (960×600 la pared y 800×720 la vasija): el SVG se dibuja en un canvas, `toBlob` lo convierte y un enlace `download` lo guarda.
- **Recompensas:** la primera obra da +15 de saber y la ficha del soporte; los símbolos descubiertos suman +2 cada uno.
- **Reto opcional «Recrea un friso al estilo de la Cueva Pintada».** Solo admite motivos de la Cueva y se pinta sobre la pared. La lista de comprobación se ve en directo:
  - 4 o más motivos en una misma fila;
  - una alternancia A-B, de motivo o de color;
  - rojo y blanco a la vez.
  - Superarlo da +15.
- **Ficha final «¿Qué significan estos símbolos?»** No se inventa ningún significado. Explica que no se sabe y separa lo documentado (formas, lugares, técnicas) de las hipótesis (calendario, linajes, marcas de grano o de propiedad), sin dar ninguna por buena.

## 3. Símbolos (27) con procedencia y fuente

Todos están redibujados y estilizados: son una interpretación escolar, no un calco.

| Grupo · se descubre en | Símbolos | Procedencia | Fuentes |
|---|---|---|---|
| **Cueva Pintada de Gáldar** · Pigmentos, «Mirar la cámara pintada» | círculos concéntricos con punto, cuadrado partido en triángulos, cuadrado partido en dos, triángulos opuestos por la base, ángulos encajados, dientes de sierra, ajedrezado, entramado de franjas | Gran Canaria, Gáldar. Pintura mural en almagre, blanco y negro sobre toba | Guía de la Cueva Pintada (MDC-ULPGC); calco digital 3D (XXIV Coloquio de Historia Canario-Americana, 2020); Zephyrus XXV (1974). La crónica habla de paredes «cuarteadas y ajedrezadas» |
| **Pintaderas** · Sala de patrimonio, vitrina | celdillas romboidales («panal»), circular de anillos, ajedrezada, triángulos en hileras, zigzag | Gran Canaria, pintaderas de barro cocido. Motivos incisos o excisos | El Museo Canario (catálogo); GEVIC; estudio morfotecnológico de las pintaderas (ULPGC, hdl 10553/21812) |
| **Cerámica pintada** · Sala de patrimonio, vitrina | triángulos colgantes del borde, metopa con triángulos opuestos, líneas onduladas, línea quebrada, diagonales paralelas, rombo doble, ángulos superpuestos, banda de metopas | Gran Canaria, vasijas bruñidas pintadas con almagre (La Cerera en Arucas, Gáldar…) | Guía de la Cueva Pintada; «Elementos simbólicos y cerámica… La Cerera» (Coloquios MDC 1629); «Cerámica funeraria en la prehistoria de Gran Canaria» (Coloquios MDC 1989) |
| **Grabados de Balos** · Almogarén, «Grabados de Balos» | signos líbico-bereberes (columna genérica, no copia una inscripción real), lagarto esquemático, serpentiforme | Gran Canaria, barranco de Balos (Agüimes), grabado picado en basalto | BOC 2002/135 (declaración BIC); «Nuevas investigaciones… barranco de Balos» (ULPGC, hdl 10553/12848) |
| **Grabados de La Palma** · Cuaderno, «Otras islas» | espiral, meandriforme, semicírculos concéntricos | La Palma: cueva de Belmaco (Villa de Mazo) y otras estaciones. Grabado picado | E. Martín Rodríguez (ULPGC), grabados de La Palma; Parque Arqueológico de Belmaco (Cabildo); dibujo del siglo XVIII de Belmaco (Biblioteca Virtual Miguel de Cervantes) |

Al empezar se tienen: círculos concéntricos, cuadrado partido en triángulos y triángulos colgantes.

**Descartados por falta de documentación o por riesgo de error:**
- **Retícula en pintaderas:** no la he podido confirmar. La trama documentada es la de rombos («panal»).
- **Espiral en pintaderas:** solo se cita una pieza, y no la he podido comprobar.
- **Antropomorfos de Balos:** son figuras humanas con rasgos sexuales exagerados, poco adecuados como «símbolo para pintar» en 1º y 2º de ESO, y su lectura es discutida.
- **Équidos y jinetes de Balos:** probablemente son posteriores a la conquista.
- **Cruciformes:** se confunden con cruces históricas posteriores.
- **Líneas incisas en la cerámica de Gran Canaria:** la cerámica de Gran Canaria es sobre todo pintada y la incisión es minoritaria. No he querido presentarla como típica.
- **Soliformes o «soles» radiados:** su nombre ya da por hecha una interpretación.
- **Diseños modernos de «pintaderas» de recuerdo.**

## 4. Partidas y migración

- `migratePaint()` se llama desde `migrate()` y solo actúa una vez (`paintMigrated`).
- Una partida antigua que ya tenía:
  - el **panel** desbloquea los 8 símbolos de la Cueva y recrea una obra de pared en la galería (con sus colores, marcada `old`);
  - la **vasija** desbloquea los triángulos colgantes y la línea quebrada, y recrea una vasija en la galería;
  - el **cuero** desbloquea la pintadera circular y el zigzag.
- `state.decor` se vacía. Los objetos antiguos que ya se habían fabricado siguen en el zurrón con su icono.
- Partida nueva: `symbols` arranca con los 3 iniciales.

## 5. Pruebas (puppeteer-core + Chrome, `file://`)

- El recorrido completo `pruebas_va/run_fase5.js` va desde la portada hasta el final e incluye:
  - jornada 1, mapa, quiz y almogarén;
  - recolección, campos, almacén, cantera y rebaño;
  - las 4 estaciones con los 14 objetos;
  - el bolsillo (tocar y arrastrar), el marisqueo, la pesca y la cocina del mar;
  - los colorantes (el rojo, empezado desde el bolsillo);
  - **descubrir los 27 símbolos**, pintar en la pared y en la vasija (arrastrar desde la paleta, mover, girar, escalar, friso, friso alterno, deshacer y borrar), PNG, galería y reto;
  - los retos del risco (salto con un fallo y dátiles), el silbo y el final.
- Se ha pasado en **1280×800 y 1920×1080 (ratón)** y en **390×844, 844×390 y 360×640 (táctil)**.
- Resultado en todos: 0 errores o avisos de consola y 0 peticiones de red.
- En móvil no hay desbordamiento horizontal ni botones de menos de 44 px.
- La descarga PNG se ha comprobado: un archivo real de 960×600 (pared); la vasija sale de 800×720.
- Migración (`pruebas_va/migra_test.js`): una partida de la fase 4 con panel, vasija y cuero y `state.decor` con colores.
  - Carga sin errores y desbloquea 12 símbolos.
  - Recrea 2 obras antiguas en la galería, que siguen ahí tras recargar.
  - `decor` queda vacío y los objetos antiguos siguen en el zurrón.
- Errores corregidos durante las pruebas:
  - En móvil vertical, el soporte no se quedaba fijo arriba: `.app-shell` tiene `overflow:hidden`, que anula `position:sticky`. Ahora usa `overflow:clip`, solo en la pantalla de pintado y en anchos de 600 px o menos.
  - En la pared recreada de una partida antigua, un motivo rojo caía sobre la banda roja y no se veía.
- Service worker `vida-aborigen-v4`, servido por http: con la red cortada vuelven a abrirse el juego y el silbo.

## 6. Limitaciones

- El **zigzag en pintaderas** solo está confirmado de forma indirecta, por el análisis espacial de las pintaderas (Coloquios MDC). No he podido abrir el catálogo de El Museo Canario desde aquí para verlo.
- Los motivos están **redibujados y simplificados**: dan una idea de la forma, no copian una pieza concreta.
- La galería se guarda aparte de la partida y en el mismo navegador. Si se borran los datos del sitio, se pierde.
- En móvil vertical el editor funciona, pero se pinta mejor en apaisado (sale el aviso de girar).
- La descarga PNG depende del navegador. En iOS puede abrirse la imagen en lugar de guardarse; entonces hay que mantenerla pulsada para guardarla.


---

# Vida Aborigen · Fase 4 (22/10/2026): bolsillo, marisqueo en los charcos y pigmentos

Mismas reglas que en la fase 3:
- Funciona en móvil y en escritorio, sin conexión, con 0 errores de consola y 0 peticiones de red.
- Las imágenes no llevan texto incrustado, y la flora y la fauna son nativas de Gran Canaria.
- No se han tocado los adjuntos originales ni las imágenes que ya existían en `img/`; solo se han añadido archivos.

Los cambios de código llevan `// FIX (fase 4)` (o `/* FIX (fase 4) … */` dentro de las funciones de una línea).

## 1. Bolsillo (acceso rápido)

- **En el marcador:** tres casillas junto a «Abrir zurrón».
  - En vertical forman una fila propia de ancho completo.
  - Todas miden 44 px o más.
- **Colocar un objeto** (desde el zurrón): toca el objeto y después una casilla, o arrástralo.
  - Con el ratón, se arrastra sin más.
  - Con el dedo, mantén pulsado un momento (250 ms) y arrastra. Así la ventana se sigue pudiendo desplazar.
  - Si arrastras hacia el borde, la ventana se desplaza sola.
- **Devolver o cambiar:**
  - Una casilla llena se toca para devolver el objeto al zurrón, o se arrastra de vuelta.
  - Si dejas un objeto en una casilla ocupada, los dos se intercambian.
- **Qué se guarda:** valen los recursos y los objetos fabricados. La casilla guarda el montón entero y el número se ve sobre el icono.
- **Uso directo** (se toca la casilla en el marcador):
  - En una estación, abre la receta pendiente que usa ese objeto (cambiando de pestaña si hace falta).
  - En el marisqueo, la **piedra** sirve para despegar lapas (si no la llevas, te prestan un canto) y la **bolsa de junco** sube la cesta de 6 a 10.
  - Con el **anzuelo de hueso** se desbloquea la pesca.
  - En las támaras, la piedra da 2 tiros extra (una vez).
  - En la decoración, el pigmento elige el color.
- **Partidas antiguas:** `migrate()` añade `pocket: [null, null, null]` y `decor: {}`. `cleanPocket()` vacía las casillas de objetos que ya no tienes.
  - Probado con una partida de la fase 3 sin bolsillo: 0 errores.
  - Una casilla con un objeto inexistente se vacía.

## 2. Marisqueo en los charcos (Playa del Marisqueo)

La Playa abre un menú con dos opciones: **Marisqueo en los charcos** (nuevo) y el **reto de saber** (el de antes).

- **Escenario:**
  - Fondo nuevo `img/playa/charcos_fondo.webp`: plataforma de basalto con charcos y algas verdes, rojas y pardas.
  - Sprites en `img/playa/`.
- **Preparar:**
  - Lo que llevas en el bolsillo cuenta.
  - Hay botones «Al bolsillo» para la piedra, la bolsa y el anzuelo.
- **Mecánica:** la **marea sube** (75 s; 110 s con movimiento reducido) y va cubriendo los charcos de arriba abajo.
  - Las **lapas** se agarran a la roca. Solo se despegan si se tocan cuando «se levantan un poco» (brillan); si no, se pegan más.
  - Los **burgados** se cogen a mano.
  - Las piezas **pequeñas** se dejan: avisa de la talla mínima actual.
  - La **carnadilla** y el **cangrejo** solo se observan.
- **Al terminar:** lapas y burgados al zurrón, +12 de saber y 6 fichas con fuentes.
  - Si llevas el anzuelo, puedes **pescar**: el burgado sirve de cebo. Hay que tirar del sedal cuando el agua salpica; si tiras antes, el pez se asusta. Se pesca una **vieja**.
- **Recetas nuevas en Medicinas y comida:** «Marisco al fuego» (lapas + fuego) y «Vieja asada».

**Especies:**

| Especie | En el juego | Por qué | Fuente |
|---|---|---|---|
| Lapas: *Patella candei crenata* (negra), *P. ulyssiponensis aspera* (blanca), *P. piperata* (curvina) | Se recogen (≥ 45 mm) | Dominan en los concheros de GC (La Fortaleza, La Cerera, El Burrero, Cueva Pintada) | Batista Galván (ULPGC); «Introducción al estudio de la malacofauna…» (ULPGC) |
| Burgado *Phorcus* (= *Osilinus*) *atratus* | Se recoge (≥ 15 mm) y sirve de cebo | Segundo en los concheros; Dumas propone *Phorcus* como carnada | Mismas fuentes; *Trabajos de Prehistoria* 2021 |
| Carnadilla *Stramonita* (= *Thais*) *haemastoma* | Solo se observa | Está en los concheros, pero hoy su marisqueo está vedado | Malacofauna (ULPGC); Gobierno de Canarias |
| Cangrejo moro *Grapsus adscensionis* | Solo se observa | Los artrópodos casi no se conservan en los yacimientos; no se afirma su consumo | Arqueomalacofaunas de Tenerife (MDC) |
| Algas | Decorado | No se conservan; no se afirma su uso | — |
| Vieja *Sparisoma cretense* | Pesca con anzuelo | Entre los peces más frecuentes en los yacimientos; Abreu cita anzuelos de cuerno de cabra | Rodríguez Santana (tesis); Abreu, libro II |

- **Herramienta:** no hay pruebas directas de con qué despegaban las lapas los antiguos canarios.
  - Junto a los concheros aparecen lascas y cantos de basalto (Coloquios, La Gomera), y por eso el juego usa una **piedra**.
  - El «lapero» de hierro es posterior a la conquista (RAE, TDHLE).
- **Sostenibilidad:** la ficha «Cuidar el marisco hoy» dice expresamente que es **normativa actual, no aborigen**.
  - Tallas mínimas: lapas 45 mm y burgados 15 mm.
  - Veda de lapas y burgados del 1 de diciembre al 30 de abril, y zonas con veda permanente.
  - Límites recreativos: 3 kg de lapas y 1 kg de burgados.
  - Fuentes: Gobierno de Canarias (tallas y vedas) y Orden de 2 de mayo de 2011.
  - No se inventa ninguna norma aborigen.

## 3. Colorantes y estación «Pigmentos» (Idaira)

- **Tierras:** en la **Cantera** hay dos vetas nuevas: **tierra de almagre** y **tierra blanca volcánica**. En **Recolectar** se consiguen **astillas de tea** (pino canario).
- **Estación Pigmentos:** cuarta pestaña del taller, con fondo nuevo `img/estaciones/pigmentos.webp`.
  - **Rojo de almagre:** almagre + molino (moler y mezclar con agua).
  - **Blanco de tierra clara:** tierra blanca + molino.
  - **Negro de hollín:** tea + fuego.
- **Usos (minijuegos, generados en SVG en el juego; no copian ninguna pintura real):**
  - **Panel geométrico**, inspirado en la Cueva Pintada: 31 figuras (círculos concéntricos, triángulos opuestos y un friso en zigzag). Se pintan con rojo, blanco o «toba sin pintar».
  - **Vasija decorada:** con una vasija de barro del Almacén.
  - **Cuero estampado con pintadera:** con cuero curtido; 6 estampas con 3 sellos inventados.

**Pigmentos y fuentes:**

| Color | Qué dice la evidencia | Fuente |
|---|---|---|
| Rojo · almagre | Tierra rica en óxidos de hierro, molida y mezclada con agua. Es el color más frecuente en la cerámica de GC y está en la Cueva Pintada | Cueva Pintada (historia y guía MDC); Sánchez-Moral et al. 2002; CanariWiki; clasificación cerámica (ULPGC) |
| Blanco · arcillas claras | Arcillas blanquecinas finas (haloisita en Gáldar) y tobas, pómez o caliche. No se usan cal ni yeso | Guía MDC; Sánchez-Moral 2002; «Procedimientos y técnicas pictóricas» (Coloquios) |
| Negro | **Debate.** En la Cueva Pintada parece la propia toba oscurecida, sin pintura. En otras cuevas hay hollín (tea), intencionado en pocos sitios. Hay cerámica con negro | ULPGC (análisis espectral); guía MDC; Técnicas pictóricas; CanariWiki |

- **Excluidos** (ficha «Colores que el juego deja fuera»):
  - **Orchilla:** tinte del comercio europeo.
  - **Púrpura:** taller romano del islote de Lobos (Museos de Tenerife).
  - No se presentan como aborígenes.
- **Otras fichas:** pintaderas (El Museo Canario: más de 200; función desconocida; estampar cuero es una recreación), vasija pintada y panel. Abreu: «había pintores, que era oficio más de mujeres que de hombres».

## 4. Arte nuevo (WebP, sin texto)

- **Fondos:** `img/playa/charcos_fondo.webp` y `img/estaciones/pigmentos.webp`.
- **Sprites de la playa:** lapa vista desde arriba, burgado, carnadilla y cangrejo.
- **Iconos:** burgado, carnadilla, vieja, almagre, tierra blanca, tea, tres pigmentos, panel, vasija pintada, pintadera, piel estampada, lapas asadas, lasca y canto.
- **Descartes:**
  - Se descartaron una lapa de perfil y unas «lapas asadas» que parecían berberechos o vieiras.
  - Las versiones sin usar están en `/workspace/fase4_arte/sin_usar/`, fuera del juego.

## 5. Correcciones durante las pruebas

- Al arrastrar con el ratón ya no se selecciona el texto de la ventana.
- El clic fantasma tras soltar se ignora solo 250 ms.
- En los minijuegos, la raya de la nota de seguridad quedaba suelta a la izquierda (también en la fase 3); ahora se ciñe al texto.
- La picada de la pesca se ve mejor.
- El aviso «Gira el móvil» ya no habla del barranco: vale para todas las escenas apaisadas.
- **Service worker:**
  - La caché pasa a `vida-aborigen-v3` con los 155 archivos.
  - Comprobado servido por http y luego sin conexión: 156 entradas en caché; el juego y el silbo arrancan.

## 6. Pruebas (Chrome headless)

- **Script:** `run_fase4.js` (en `/tmp/va/`, fuera del juego, junto con `mig4.js` y `sw_test.js`) recorre todo el juego:
  - Fases nuevas: bolsillo (tocar, arrastrar, intercambiar), marisqueo, pesca, cocina del mar, los tres pigmentos (el rojo, empezado desde el bolsillo) y los tres usos.
  - Regresión de las anteriores: jornada 1, mapa, retos, estaciones, salto del pastor, escena, támaras, cuaderno, silbo y final.
- **Pantallas:**
  - 1280×800 y 1920×1080 con ratón.
  - 390×844, 844×390 y 360×640 con emulación táctil.
- **Resultado:** 0 errores de consola, 0 peticiones de red y ningún desbordamiento horizontal. En móvil, ningún botón mide menos de 44 px.
- **Capturas:** en `capturas/fase4/`.

## 7. Datos que no se han podido confirmar (y cómo se tratan)

- La herramienta aborigen para las lapas: se usa una piedra y se explica la duda.
- El negro de la Cueva Pintada (toba sin pintar o pigmento): se presenta como debate.
- El aglutinante: mezclar con grasa es una propuesta experimental. El juego solo usa agua.
- La función de las pintaderas es desconocida.
- No se afirma que comieran cangrejos ni algas.
- La veda de la carnadilla está vigente según la información del Gobierno de Canarias consultada; conviene revisarla cada temporada.
- La datación exacta del comercio de la orchilla en Gran Canaria.

## 8. Limitaciones

- Los sprites son ilustraciones generadas y estilizadas, no dibujos científicos.
- En el móvil en vertical, los charcos se ven pequeños; se recomienda girarlo (aparece el aviso).
- En el móvil, con el bolsillo, el marcador ocupa una fila más.
- Las normas de marisqueo cambian: la ficha remite a la normativa vigente.

---

# Vida Aborigen · Fase 3 (21/10/2026): rigor histórico, tres estaciones y retos del risco

Orden aprobado: 1) rigor, 2) estaciones, 3) minijuegos. Los cambios de código llevan comentarios `// FIX (fase 3)` (o `/* FIX … */` dentro de las funciones de una línea). Los adjuntos originales no se han tocado; el guion corregido es una copia en `docs/GUION_revisado.md`.

## 1. Rigor histórico (antes → después, con fuente)

| Tema | Antes | Después | Fuente |
|---|---|---|---|
| Gobierno | El guaire aparecía como jefe | Gobernaba el **guanarteme** (Gáldar y Telde); los **guaires** eran consejeros o nobles del Sabor; el **faycán** era la segunda persona y dirigía los ritos. Nueva ficha «¿Quién decidía?» en el Pueblo | Abreu Galindo, libro II («doce consejeros… que llamaban Gayres»); *Revista de Historia Canaria* 208 (ULL, 2026) |
| Enterramientos | Momias asociadas al almogarén | Difuntos en **cuevas y túmulos**; el almogarén es un lugar de culto. Ficha «Enterramiento» | AEA (prácticas funerarias); Cabildo GC: Maipés de Agaete y Arteara |
| Perro | Sin matiz (riesgo de identificarlo con el presa o el garafiano) | «**Perro aborigen**», sin razas actuales | Alberto-Barroso et al. (Museos de Tenerife) |
| Fibras | Telar | **Trenzado y cestería** de junco y palma: esteras, sogas y bolsas | El Museo Canario (fibras y pieles); Abreu Galindo («hacer esteras de hojas de palmas y sogas de juncos») |
| Gara y Jonay | Presentada como leyenda | «**Leyenda gomera posterior** (no aborigen)»: tradición oral, versiones escritas del siglo XX y nombres tomados del topónimo Garajonay. Cambiado en `silbo/silbo.js`, `silbos.js` y `silbos.json` (copia del proyecto) | Trapero, ULPGC (*Guanchismos*); MDC |
| Banot | «Banot de viaje» | **Garrote / palo de pastor**. «Banot» es un término de Tenerife; las partidas guardadas se convierten solas | RAE (*banot*); Federación de Salto del Pastor Canario |
| Salto del pastor | Vara genérica | En Gran Canaria se usa el **garrote** (lanza en Tenerife, astia en La Gomera); la punta antigua se endurecía al fuego o era de cuerno. BIC desde 2018 | FSPC; BOC 2018/104 (Decreto 83/2018) |
| Navegación | Debate con minijuego opcional de odre en el guion | **Sin navegación ni tablas.** Ficha «Viajar entre islas: lo que no sabemos» | Serrano et al., *Nature Communications* (2023); RHC 208 |
| Anzuelo | Se encontraba en la playa | Se **fabrica** en la estación de madera y piedra; la playa da lapas | El Museo Canario, reg. 29.915 (Cendro, Telde) |
| Gofio | «hasta mediados del siglo XX» | «sigue formando parte de la cocina canaria» | El Museo Canario (economía) |
| Ungüento | Receta genérica «planta + vasija» | Recetas citadas: remedio de la crónica (junco majado y manteca de cabra), arrope de mocán y polvo de sangre de drago, con **aviso educativo** | Abreu Galindo, libros II y III; MDC (mocanes, drago) |

Cuando un dato procede de otra isla se dice en la ficha: el fuego por frotación aparece en la crónica de Lanzarote y Fuerteventura (Abreu, libro I, cap. X), y el arrope de mocán, en la de Tenerife (libro III, cap. XII), aunque el mocán también crece en Gran Canaria.

## 2. Tres estaciones de taller

- **Madera y piedra:** molino de mano (se conserva la lógica de pulido), anzuelo de hueso y garrote (necesita fuego).
- **Secado y curtido:** cuero curtido, estera de palma y bolsa de junco.
- **Medicinas y comida:** fuego (pulsar o mantener para «Frotar el palo»), gofio (cebada + molino + fuego), arrope de mocán, remedio de la crónica y polvo de sangre de drago.

Cada estación es una pestaña táctil con su fondo (`img/estaciones/`), un personaje (Nauzet o Fayna) y tarjetas de receta. Las tarjetas muestran fichas de materiales verdes o rojas, las herramientas y el botón «Ficha y fuentes». Las recetas que no se pulen se hacen en tres pasos con un dato en cada uno.

Recursos nuevos: hueso y manteca (Rebaño), palma y resina de drago («sin herir el árbol»), lapas (Playa) y mocán (Bosque). Las fichas nuevas son: gobierno, enterramiento, islas, anzuelo, garrote, fuego, cuero, estera, bolsa, arrope, cura, drago y dátiles. Las fuentes con enlace se reúnen en `SRC` (`game.js`). La función `migrate()` actualiza las partidas antiguas.

## 3. Retos del Camino del Risco (`img/risco/`)

- **Salto del pastor:** tiene una barra de ritmo y cinco rellanos. La figura del pastor salta y la cabra va delante. Se juega con toque, clic, Intro o Espacio. Al fallar, la escena tiembla y se reintenta. Con movimiento reducido, la zona es más ancha y la marca va más lenta. Al ganar se ve una escena de 3 cuadros, con los textos en HTML, que avanza sola y se puede saltar.
- **Támaras de la palmera canaria:** tirachinas táctil (arrastrar y soltar) o deslizadores de ángulo y fuerza, con trayectoria de puntos. Hay que bajar 3 racimos con 8 piedras. Se basa en Abreu: «de una pedrada derribaba… un racimo de dátiles».
- **Arte nuevo:** sin texto incrustado y con flora nativa (dragos, cardones canarios, tabaibas, pinos y palmera canaria; sin tuneras, pitas ni cactus americanos), en WebP. Los racimos son sprites aparte.

## 4. Correcciones durante las pruebas

- En el móvil, el «clic fantasma» del último toque al pulir pulsaba «Volver». Ahora se ignora durante 600 ms y el foco no desplaza la pantalla.
- Se evita un `NaN` en la trayectoria cuando la escena aún no tiene tamaño.
- La caché del service worker pasa a la versión `vida-aborigen-v2` y su lista incluye los 133 archivos del juego (comprobado sin conexión: 134 entradas en caché).

## 5. Pruebas (Chrome headless)

Se ha recorrido cada fase con capturas en `capturas/fase3/` en 1280×800, 1920×1080, 390×844, 844×390 y 360×640 (estos tres, táctiles). El resultado es **0 errores de consola y 0 peticiones de red**.

## 6. Limitaciones

- El «bolsillo» de 3 huecos (opcional) no se ha hecho.
- En el móvil en vertical, los minijuegos del risco se ven pequeños; se recomienda girarlo.
- Algunas fuentes son crónicas de otras islas y se indica en la ficha.
- `run_final.js` y `run_movil.js` (pruebas antiguas) usan la receta «Banot» y han sido sustituidas por `run_fase3.js`.

---

# Vida Aborigen · Registro de cambios (versión final integrada, 20/10/2026)

Esta carpeta es una copia nueva. No se ha tocado `/workspace/vida_aborigen/` (la versión corregida), ni `/workspace/vida_aborigen_arte/` ni `/workspace/silbo/`: de esas carpetas solo se ha leído y copiado. Cada cambio de esta fase va comentado en el código con `// FIX (final):` (o `/* FIX (final): */` en el CSS y `<!-- FIX (final) -->` en el HTML). Los comentarios `// FIX:` sin «(final)» vienen de la versión corregida. Su historial está al final de este documento.

## A. Arte nuevo sin texto (de `vida_aborigen_arte/`)

| Pantalla | Imagen (img/) | Cómo se integra |
|---|---|---|
| Portada | `portada_amanecer.webp` | Fondo de la portada. La tarjeta va abajo para no tapar el cielo. |
| Elige tu camino | `fondo_elige_camino.webp` + `tarjeta_risco/taller/almogaren.webp` | Las tarjetas son 4:3 y el fondo va bajo un velo de pergamino. `SCENES.camino` lleva `baked:false` y capas en las posiciones de ARTE.md. |
| Personajes | `fondo_personajes.webp` + `gaire_retrato.webp` / `tayda_retrato.webp` | Retratos de cuerpo entero en las tarjetas. Ya no hace falta recortar la ilustración antigua. |
| Mapa | `mapa_dia.webp` | `baked:false`. El título, las 11 etiquetas y la «Sala de patrimonio» son capas HTML con las coordenadas de ARTE.md. El mapa se muestra en modo **contain**, con proporción fija 896:1195 y ajustado al alto de la ventana. |
| Jornada 1 | `portada_amanecer` (encargo y cierre), `j1_rastreo_barranco`, `j1_decision_cabra` (panel a la derecha), `j1_salto_pastor` (panel a la izquierda y aviso «Hoy se aprende con monitores…») | Cada escena coloca su panel en la zona libre que indica ARTE.md (`panel: 'left'/'right'/'center'`), con velo degradado solo en esa zona. |
| Rastreo | `j1_rastreo_barranco.webp` + `iconos/*.webp` | El barranco nuevo ya no trae indicios pintados. Por eso las pistas vuelven al orden y a las coordenadas originales del código, y cada una usa su icono suelto. |
| Retos | `j3_costa` (Playa), `j2_laurisilva` (Bosque), `j5_cielo` (Almogarén) | Panel lateral según ARTE.md. Lo que no tiene escena propia usa `almogaren_nocturno`. |
| Taller y pulido | `j4_taller.webp` | Panel en la franja izquierda libre. |
| Almacén | `j4_almacen.webp` | Imagen de cabecera en la ventana. |
| Sala de patrimonio | `carta_idolo_tara.webp` (sin marco) + `pintaderas_mesa.webp` | Capas de ARTE.md: «Conocido popularmente como / Ídolo de Tara», la cartela «Gran Canaria · sin datación directa · Recreación», «Observar con lupa» y «Saber más». Lleva además el **sello «Recreación»**, una capa HTML girada en la esquina de la carta. |
| Diálogos | `npc_areguia.webp`, `npc_guayarmina.webp` | Retrato circular de quien habla. |
| Final | `final_noche_compartida.webp` | Nueva pantalla «La noche compartida» (ver C). |
| Zurrón | `iconos/*.webp` | Los 10 recursos usan iconos sueltos del arte nuevo, en estilo plano y transparentes. **Cebada**, **piedra volcánica porosa** y **molino** se regeneraron en ese mismo estilo para que no desentonen. La lámina `resource-icons.webp` queda solo como respaldo del CSS. |

- **«Templo» pasa a llamarse «Almogarén»** en el mapa, en el reto y en el marcador.
- **Cebada:** el mapa nuevo pinta bancales junto al pueblo, y ARTE.md los rotula «Campos de cebada». Por eso la cebada ahora **se siega en los Campos** (una vez), en vez de tomarse del Almacén como en la versión corregida. El Almacén (cueva-granero) queda como reserva comunitaria y presta la vasija. «Recolectar» se coloca junto a los dragos y el palmeral, y la **Cantera** en la ladera del volcán.
- La lógica del molino y del gofio no cambia: piedra porosa de la Cantera, pulido en el taller (clic, Intro o Espacio, o mantener pulsado, con `prefers-reduced-motion`), gofio = cebada + molino (herramienta que no se gasta).

## B. Minijuego del silbo (v2) integrado

- Se ha copiado de `/workspace/silbo/prototipo/` a `silbo/` (el original no se toca) y se abre desde el mapa: botón «Ecos de La Gomera · silbo» y, siguiendo el guion (J2.3 «Silbo a distancia»), el botón «Oír un silbo a distancia ›» al resolver el reto del Bosque.
- **Fuentes compartidas:** la copia del silbo ya no lleva fuentes propias y enlaza `../fonts/fonts.css`. Los archivos eran idénticos (mismo md5). Las licencias OFL quedan en `fonts/`.
- **Partida compartida:** `silbo/puente.js` es un archivo nuevo que no altera la lógica del minijuego.
  - Lee la partida, `vida-aborigen-partida-v1`, y usa el mismo personaje (Gaire o Tayda).
  - Al completar la conversación suma +10 de saber **una sola vez**, marca `done.silbo` y añade la ficha «El silbo gomero» al Cuaderno.
  - Pone «← Mapa» en la barra y «Volver al mapa del pueblo» en la pantalla final.
  - Al volver, `index.html?volver=mapa` reanuda la partida directamente en el mapa.
- **Estilo:** el silbo ya compartía paleta, tipografías y patrón de código. Solo se añade el estilo del botón de vuelta.
- **Créditos de audio intactos:** la pantalla © del silbo, `audios/atribucion.csv` y `audios/LICENCIA.md` no se han modificado.

## C. Final común «La noche compartida»

Aparece en el panel del mapa cuando se han hecho los tres retos de saber y el gofio. El silbo es opcional. El texto sale del guion:

- la entrada final del Cuaderno, **«Vivir es relacionarse»**;
- la frase de Areguía, «Hoy no has traído respuestas para cerrar la historia…»;
- la variación según el camino elegido;
- con confianza alta, la frase «Lo que aprendiste no se queda en tu zurrón…».

## D. Imágenes en WebP

- Todas las imágenes del juego y del silbo son WebP (calidad 82, `method=6`). En el silbo se convirtieron `fondo_barranco_noche`, `pergamino` y `marco_madera`, y `silbo.css` se ajustó a esas rutas.
- No queda ningún PNG, JPG ni `Gemini_Generated_Image_*` referenciado. `img/` ocupa unos 3,6 MB y el zip, mucho menos que los 25 MB de la versión corregida.

## E. Pruebas

Recorrido completo automatizado en Chrome headless a **1280×800** y **1920×1080**:

- portada, camino, personaje y toda la Jornada 1 (con la pista falsa y Escape);
- mapa, los tres retos, Campos, Almacén, Cantera (error y acierto) y Recolectar;
- taller: gofio sin molino (aviso), pulido con ratón, teclado y pulsación mantenida, molino, gofio y ungüento;
- zurrón, Cuaderno, patrimonio con el sello y las pintaderas, Casa, Pueblo y Rebaño;
- silbo: ida, créditos, una ronda, final, ficha y vuelta al mapa;
- final «La noche compartida»;
- recarga y «Continuar».

Resultado en ambas resoluciones: **0 errores de consola, 0 peticiones de red**. Las fuentes se cargan en el juego y en el silbo. Capturas en `capturas/`.

## F. Limitaciones conocidas

- No se usa el mapa nocturno (`03b`); el juego solo tiene el mapa de día.
- Los retratos del silbo (Gaire, Tayda e Iballa) siguen siendo los del prototipo, recortados del arte anterior. Encajan, pero no son los retratos nuevos.
- Los defectos de arte que recoge ARTE.md siguen ahí:
  - el ídolo tiene rasgos estilizados (por eso lleva el sello);
  - la concha parece un caracol;
  - el icono de piel conserva la cabeza de la cabra.
- Siguen sin escena propia (no se generaron): el embarbascado, las tres variantes de final por camino y el epílogo de conquista.
- El juego cubre la Jornada 1 completa y una Jornada 2 «hub» con retos. Las jornadas 3 a 5 del guion se representan con sus escenas en los retos, no como jornadas completas.
- En `file://`, Chrome comparte el localStorage entre archivos locales: la partida se comparte entre el juego y el silbo, como se pretende.

## G. Móvil y tableta (21/10/2026)

He probado el juego y el silbo con emulación táctil en Chrome headless. Las pantallas probadas son 360×640, 390×844 y 412×915, en vertical y en apaisado, y la tableta a 768×1024 y 1024×768. En escritorio se ha vuelto a comprobar 1280×800 y 1920×1080. Todos los cambios llevan el comentario `FIX (móvil)`.

- **Viewport y notch:**
  - `viewport-fit=cover` y `theme-color` en `index.html` y `silbo/index.html`.
  - Márgenes seguros con `env(safe-area-inset-*)` en la cabecera, el marcador, las ventanas, el aviso y el silbo.
  - Las alturas pasan de `vh` a `dvh` (con `vh` de respaldo). La variable `--chrome` guarda el alto real de cabecera y marcador; `game.js` la mide en cada pantalla, al cambiar de tamaño y al girar.
- **Sin cortes ni desplazamiento horizontal:** hay maquetas propias para móvil en vertical (≤ 600 px), móvil en horizontal (alto ≤ 500 px) y tableta (601–900 px). El escritorio no cambia. En todas las pantallas probadas, `scrollWidth` es igual al ancho de la ventana y ningún botón visible queda fuera.
- **Objetivos táctiles de 44 px como mínimo** en pantallas táctiles o estrechas. Esto incluye botones, respuestas, iconos, cierre «×», indicios del rastreo, controles del silbo y la casilla del modo por parejas. El recorrido mide en cada captura los elementos que quedan por debajo de 44 px: **0**.
- **Capas de SCENES alineadas:** en táctil, las etiquetas y botones pintados sobre las ilustraciones son un botón transparente de 44 px con la «píldora» visible dentro. El texto sigue en su sitio sobre la imagen y la zona de toque crece.
- **Mapa en el móvil:**
  - En vertical se muestra primero el mapa entero, luego el panel de la jornada y después una **lista de «Lugares del mapa»** con botones grandes que hacen lo mismo que tocar la ilustración.
  - En horizontal y en tableta, el panel y la lista van a la izquierda y el mapa a la derecha.
  - Las etiquetas largas (Playa del Marisqueo, Bosque de laurisilva, Almacén) pasan a dos líneas para no salirse del mapa.
- **«Gira el móvil»:**
  - El rastreo del barranco (escena apaisada) muestra en vertical un aviso con un móvil que gira. El aviso respeta `prefers-reduced-motion`.
  - Al girar, el aviso desaparece y la escena se ve entera; el marcador se oculta para ganar alto.
  - Con «Seguir en vertical» se juega en una maqueta apilada (escena arriba, textos y «Continuar» debajo). Sirve, por ejemplo, si el giro de pantalla está bloqueado.
  - Las demás pantallas funcionan en vertical sin aviso.
- **Pulir el molino con el dedo:**
  - Se usan pointer events con `setPointerCapture`, de modo que el dedo puede moverse un poco sin cortar el pulido.
  - `touch-action:none`, `user-select:none`, `-webkit-touch-callout:none`, sin menú contextual y sin arrastrar las imágenes.
  - Un toque corto suma +10 %; mantener pulsado suma +3 % cada 140 ms.
- **Nada depende del hover ni de Escape:**
  - Las ventanas se cierran con «×» (44 px) o tocando fuera. Escape sigue funcionando con teclado.
  - En el rastreo, la ficha del indicio aparece al tocarlo. En pantallas pequeñas se ocultan los globos de hover y se usa el recuadro inferior.
  - Con `@media (hover:none)` se anulan los efectos que se quedaban «pegados» tras tocar.
  - He cambiado los textos que decían «pasa el cursor» o «tecla Escape».
- **Silbo:**
  - Barra compacta en horizontal. La ronda va en una columna central con desplazamiento propio y los personajes quedan a los lados.
  - Maqueta apilada en vertical, botones de 44 px y avisos que no bloquean los botones.
  - **Audio en iOS:** `silbo/audio-movil.js` (archivo nuevo, antes de `silbo.js`) crea 8 elementos de audio reutilizables y los desbloquea con el primer toque (touchend/pointerup/click/tecla), reproduciendo un instante de silencio generado en memoria, sin archivos ni red. Después `new Audio()` devuelve uno de esos elementos ya desbloqueados, así que suenan también los silbos que se reproducen tras una espera. iOS ignora el volumen, así que allí el eco se silencia en vez de sonar tan fuerte como la grabación original. `silbo.js` no se ha modificado.
- **Instalar como app sin conexión (opcional):**
  - `manifest.webmanifest`, `sw.js` e iconos en `icons/`. Los iconos son nuevos, de modo que `img/` no se ha tocado.
  - Solo se activa si el juego se sirve por **http(s)**: abierto como archivo local no se carga ni el manifest ni el service worker.
  - Probado con un servidor local: el service worker guarda en caché los 107 archivos y, ya sin conexión, cargan el juego y el silbo.
- **Limitaciones de la parte móvil:**
  - La emulación de Chrome no es un iPhone real: el desbloqueo del audio en iOS se ha comprobado en Chrome, pero no en Safari de iOS.
  - El service worker guarda una lista fija de archivos: si se añaden o renombran archivos, hay que actualizar la lista `ASSETS` y subir la versión `CACHE` de `sw.js`.
  - En horizontal en un móvil pequeño, el mapa y la ronda del silbo necesitan desplazamiento vertical.
- **Resultado:** 8 tamaños × recorrido completo (portada → Jornada 1 → mapa → retos → recursos → pulido táctil → zurrón, Cuaderno y patrimonio → silbo con una ronda → vuelta → final), con **0 errores de consola y 0 peticiones de red**. Capturas en `capturas/movil/`.

## H. Retratos de Fayna e Idaira y cardón en el barranco

- **Fayna** (conocedora de plantas) habla con su retrato en el reto del Bosque (guion J2.1) y en el de la Playa (J3.2, embarbascado como conocimiento histórico).
- **Idaira** (guardiana del almogarén) habla en el reto del Almogarén (J5) y en la Sala de patrimonio («Mira la postura, el material y las marcas…»).
- Los retratos usan `img/npc_fayna.webp` y `img/npc_idaira.webp` recortados al rostro, con un tamaño menor en el móvil.
- **Cardón en `j1_rastreo_barranco.webp`:** la pista del ave (68 %/58 %) sigue a la vista, en el suelo delante de la base de las matas, y se toca bien en escritorio, en tableta y en el móvil en ambas orientaciones. **No ha hecho falta mover el punto.** Las demás pistas tampoco quedan tapadas.

---

# Historial · versión corregida (cebada, molino y correcciones previas)

Base: los archivos originales `index.html`, `game.js` y `styles.css`, que no se han modificado. Esta copia corregida está en esta carpeta.
Las referencias «original Lxx» usan la numeración del archivo entregado, igual que el informe. Las referencias «ahora Lxx» son de la versión corregida. Cada cambio del código lleva un comentario `// FIX:` (o `/* FIX: */` en el CSS).

## 1. Proyecto reconstruido con los nombres que espera el código

| Archivo que pide el código | Origen |
|---|---|
| `Gemini_Generated_Image_(2).png` | Pantalla «Elige tu camino» |
| `Gemini_Generated_Image_(3).png` | Pantalla de personajes |
| `Gemini_Generated_Image_(4).png` | Mapa principal |
| `Gemini_Generated_Image_(5).png` | Escena nocturna de las pintaderas (arte del Camino del Taller) |
| `Gemini_Generated_Image_(6).png` | Carta del Ídolo de Tara |
| `Gemini_Generated_Image_(7).png` | Almogarén nocturno (portada y actividades) |
| `assets/jornada1-rastro.png` | Paisaje del barranco (1672×941) |
| `assets/jornada1-pruebas.png` | Lámina de pistas de rastreo (3×2) |
| `assets/resource-icons.png` | Lámina de iconos del zurrón (4×2) |
| `fonts/*.woff2` | DM Sans y Playfair Display (licencia OFL, ver `fonts/LICENCIA.txt`) |

## 2. Fallos corregidos

| # | Fallo | Causa | Corrección | Dónde |
|---|---|---|---|---|
| 1 | El botín del reto se entregaba al entrar, sin responder, y se podía acumular sin límite | `addItem(loot)` se llamaba antes de pintar la pregunta | El objeto y el +10 de saber se dan solo con el **primer acierto**. El reto queda marcado en `state.done` y, si se repite, se avisa de que no suma | game.js original L62 → ahora L179 |
| 2 | Cada acierto adelantaba una jornada (se llegaba al día 5 con 102 de saber) | `state.day = Math.min(5, state.day + 1)` en cada respuesta correcta | Las preguntas ya no cambian la jornada. Solo avanza al completar el objetivo (la jornada 1 deja la 2) | original L62 → ahora L179 |
| 3 | Madera, piedra y támara no se podían conseguir: Banot y Gofio eran imposibles | Ninguna actividad entregaba esos recursos | El lugar «Recolectar» del mapa abre una recogida única de madera ×1, piedra ×2, támara ×1 y junco ×1 | original L59/L65 → ahora L172-173 |
| 4 | Lo fabricado no entraba en el zurrón y el +15 se podía repetir | La receta solo restaba materiales y desactivaba el botón en esa vista | `state.crafted` guarda el objeto, que aparece en «Objetos fabricados» del zurrón. Cada receta se fabrica y puntúa una vez, y sigue marcada al volver | original L65 → ahora L183, L186 |
| 5 | Aparecía «Camino del Risco · null» en el marcador | Plantilla `${state.path.title} · ${state.character}` con el personaje aún vacío | Se omiten las partes vacías | original L15 → ahora L93 |
| 6 | Lugares del mapa mal asignados: «Recolectar» abría la Playa, «Almacén» abría el zurrón, Pueblo y Taller hacían lo mismo | Asignaciones cruzadas en `hotspot()` | Taller → taller; Pueblo → encargos de la jornada; Casa → estado del viaje y borrar partida; Recolectar → recogida; Almacén → reserva comunitaria (presta una vasija una vez); el zurrón pintado del mapa abre el zurrón | original L59 → ahora L168-175 |
| 7 | La «Huella de cabra» mostraba la huella de ave (y la hierba mostraba la pezuña) | El orden del array `clues` no seguía la lámina, y el CSS asigna los sprites por índice | Array reordenado según la lámina: rama, piedra, hierba / pezuña, ave, concha. Probado: «Huella de cabra» = posición `0 100%`, la pezuña | original game.js L38-43 y styles.css L19 → ahora game.js L131-139 |
| 8 | Iconos del zurrón partidos: cada casilla mezclaba dos | La lámina es 4×2, pero el CSS la trataba como 2×2 (`200% 200%`). Los sprites 4-7 repetían los 0-3 con filtros de color | `background-size: 400% 200%`, posiciones cada 33,333 %, sin filtros. Se quita el glifo Unicode superpuesto | styles.css original L15 → ahora L19-20; game.js original L67 → ahora L186 |
| 9 | No había guardado: al recargar se perdía la partida | No existía | `localStorage` (clave `vida-aborigen-partida-v1`) guarda solo el progreso: camino, personaje, saber, jornada, objetos, fichas y retos. **Ningún dato personal.** La portada ofrece «Continuar partida» / «Nueva partida», y «Casa» permite empezar de nuevo. Si el navegador bloquea el almacenamiento, se juega igual sin guardar | ahora L86-90, L107-109, L170 |
| 10 | Escape no cerraba las ventanas | No había gestor de teclado | Escape y un clic fuera de la ventana la cierran. El foco va al «×» al abrir y vuelve al botón de origen al cerrar. `role="dialog"`, `aria-modal` y `aria-label` en el HTML | game.js ahora L98-104; index.html L23-24 |
| 11 | Lugares del mapa invisibles hasta pasar el ratón (imposible en pizarra táctil) | `.hotspot{color:transparent}` y `span{opacity:0}` | Etiquetas HTML en pergamino **siempre visibles**, colocadas sobre las pintadas, con un **pulso sutil** (desactivado si el sistema pide reducir movimiento) y ✓ en los retos hechos. Los indicios del rastreo también laten | styles.css original L20 → ahora L35-39 |
| 12 | Fuentes cargadas de Google Fonts: sin conexión no había tipografía y se enviaba la IP del alumnado a un tercero | `@import` externo | Fuentes WOFF2 dentro de `fonts/` con `@font-face`. Probado: 0 peticiones de red | styles.css original L1 → ahora L1-5 |
| 13 | Textos en inglés en la carta del Ídolo («Information», «…no la upright de antes») | Texto pintado en la ilustración `(6)` | Cartelas HTML en español tapan el texto pintado: título «Ídolo de Tara · Recreación ilustrada» (sin «auténtico»), «Información» y un texto prudente sin la datación «s. XIII-XV». Los botones pintados «Ver detalles» y «Cerrar» ahora funcionan | game.js ahora L52-59, L165 |
| 14 | Mapa deformado | `height:1050px` + `background-size:100% 100%` estiraban la imagen vertical | Escena con la proporción real (896×1195) y panel lateral con el título, que ya no tapa el pintado | styles.css original L20 → ahora L25-26; game.js ahora L162-163 |
| 15 | Indicios del rastreo descolocados según el tamaño de la ventana, y duplicados con los pintados | Fondo `cover` en una caja de alto fijo | Escena con la proporción real (1672×941). Los indicios se colocan sobre los elementos pintados (rama, hierba junto al agua, huellas, concha) | styles.css ahora L24; game.js ahora L130-153 |
| 16 | En personajes, las dos tarjetas mostraban la imagen entera con ambos personajes | La imagen cabía entera en la tarjeta (`object-position` no recortaba) | Cada retrato recorta solo a su personaje, con nombre accesible | game.js ahora L119-126; styles.css ahora L40-41 |
| 17 | Descripciones con sesgo de género («Rastreador» / «Recolectora») que contradecían «comparten capacidades» (R1) | Texto | Texto neutro e igual para ambos: «Observa el territorio, cuida el rebaño y conoce las plantas.» | original L30 → ahora L123 |
| 18 | La pantalla final de la jornada 1 decía siempre «+20 saber» | Valor fijo | Se calcula lo ganado de verdad (`state.j1Start`) | original L55 → ahora L159-160 |
| 19 | `state.items.piel = 1` sobrescribía en lugar de sumar; los indicios falsos no se explicaban | Asignación directa; sin respuesta al jugador | `addItem('piel')`. Si se eligió algún indicio falso, una ventana explica cuál y por qué | original L48 → ahora L145-153 |
| 20 | El Templo entregaba una «Vasija de barro» (enseñaba a coger piezas de un lugar de memoria, R4) | `loot.templo = 'ceramica'` | El Templo no entrega objetos: desbloquea la ficha «Cómo sabemos lo que sabemos», que antes nunca se desbloqueaba. La vasija se consigue prestada en el Almacén | ahora L179, L174-175 |
| 21 | El aviso (toast) invisible bloqueaba los clics en la parte inferior central | Seguía encima con opacidad 0 | `pointer-events:none`; además se anuncia en lectores de pantalla (`aria-live`) y no se corta si se encadenan dos avisos | styles.css ahora L45-46; index.html L22; game.js L94-95 |
| 22 | Fondos repetidos en mosaico (dos lunas) y texto pintado («ROCA SAGRADA», «MOMIAS») compitiendo con la interfaz; texto claro sobre crema ilegible mientras carga la imagen | Sin `background-size`; sin velo | `cover` y un velo oscuro en las escenas de actividad y personajes. Subtítulo con fondo propio | styles.css ahora L40-41, L47-48 |
| 23 | Detalles menores | — | Al deseleccionar un indicio, «Continuar» se vuelve a ocultar. El salto del pastor no suma dos veces. `state.pathId` guarda el camino (necesario para efectos futuros). Botón de sonido con `aria-pressed` | game.js L117, L144, L157 |

## 3. Preparado para el arte nuevo sin texto (escenas con capas)

- `SCENES` (game.js L17-60) describe cada pantalla: `img`, `ratio` (píxeles), `crop` opcional y `layers` con `type` (`title`, `cartela`, `label`, `button`, `hotspot`), `text`, `x`/`y` (centro en % de la imagen completa), `w`/`h` y `size` opcionales, `action` y `painted` / `cover`.
- `renderStage()` (L64-75) pinta la imagen y las capas en pergamino. Los tamaños de letra van en `cqw`, así que todo escala con la escena (pizarra, 1280 o 1920).
- Las capas `painted: true` duplican un texto que ya está pintado y se ocultan mientras `baked: true`. Al recibir una ilustración sin texto basta con cambiar `img`/`ratio`, poner `baked: false` y ajustar `x`/`y` según ARTE.md.
- El mapa, el rastreo y la carta del Ídolo ya se pintan como escenas. Camino y personajes siguen con la maqueta de tarjetas (`layout: 'cards'`), porque sus ilustraciones actuales traen el texto pintado. Su configuración de capas ya está escrita (posiciones aproximadas). Se activa con `layout: 'stage'` o abriendo `index.html?escena=stage` (capturas 19 y 20).

## 4. Pruebas

- Chrome headless (puppeteer) a 1280×800 y 1920×1080, con una partida completa: portada → camino → personaje → jornada 1 (rastreo con un indicio falso, decisión, salto) → mapa → los tres retos (fallo + acierto, repetición sin premio) → recolectar → almacén → fabricar las tres recetas → zurrón → cuaderno → patrimonio (Ver detalles / Cerrar) → casa, pueblo, rebaño, zurrón → recargar → «Continuar partida».
- Resultado en ambas resoluciones: **0 errores ni avisos de consola, 0 recursos rotos y 0 peticiones de red** (funciona sin conexión). Las fuentes locales cargan y no queda texto visible en inglés ni «null».
- Valores comprobados: tras la jornada 1, jornada 2 y saber real (+17 con un indicio falso). Entrar tres veces a la Playa sin responder ya no da objetos. Los retos repetidos no suman. Sigue en jornada 2 tras todos los retos. Las tres recetas se pueden fabricar y aparecen en el zurrón. La partida se restaura igual tras recargar.
- Capturas en `capturas/` (prefijos `1280x800_` y `1920x1080_`).

## 5. Lo que NO he tocado, y por qué

- **Anacronismos y errores en las ilustraciones** (tuneras, pitas y saguaros en camino, personajes, mapa y barranco; templo clásico en personajes; momias en el almogarén y en el mapa; postura del Ídolo; iconos del anzuelo «hei matau», támaras como dátiles, «mocán» con flor amarilla). Requieren arte nuevo (R9, R10). Solo se taparon con HTML los textos erróneos de la carta del Ídolo.
- **Texto pintado en el mapa** («MOMIAS», «REZAR», «PIEL»…, que no responden) y en camino y personajes. Queda pendiente del arte sin texto; el código ya está listo para recibirlo.
- ~~Receta del gofio~~: corregida, ver apartado 6.
- **Contenido educativo** (fichas, preguntas, opciones de la decisión J1.3, nombres de personajes, «Isla de Gran Canaria»): sin cambios, salvo los textos de los puntos 13 y 17.
- **Mecánicas de medio plazo** del informe: salto con barra de precisión, rastreo por inferencia, sellos y confianza visibles, efectos reales de cada camino, panel docente, modo pizarra, `<dialog>` nativo, contenido en JSON. Cambian el diseño, así que quedan fuera.
- **Botón de sonido**: sigue sin controlar audio, porque no hay pistas de sonido en el material. Solo guarda la preferencia.
- **El vídeo de transición (R11)** no está integrado en este prototipo.
- **Peso de las imágenes**: unos 22 MB en PNG. Se mantienen los nombres y la calidad originales para no cambiar lo que espera el código. Convertirlas a WebP (R12) reduciría el peso en torno a un 80 %, pero obliga a cambiar las rutas. Conviene hacerlo cuando llegue el arte definitivo.
- **La «x/8» del zurrón** sigue contando tipos de recurso, como en el diseño original.

## 6. Cebada, cantera, molino de mano y gofio (aprobado por el usuario)

| Cambio | Detalle | Dónde |
|---|---|---|
| Receta del gofio corregida | Antes: «Gofio = támara + piedra» (incorrecto). Ahora: **Gofio = cebada (tostada) + molino de mano**. El molino es una **herramienta y no se gasta**; sin molino, el taller avisa de que hay que fabricarlo primero | game.js `recipes`, `canCraft`, `finishCraft` |
| Recurso nuevo: **cebada** | Se toma una vez en el **Almacén (cueva-granero)**. Es lo más fiel: en Gran Canaria el cereal cosechado se guardaba en graneros colectivos y de ahí salía el consumo diario. Además, el mapa ya rotula ese lugar como «Almacén · Cueva-Granero» | game.js `storehouse()` |
| Recurso nuevo: **piedra volcánica porosa** | Lugar nuevo **«Cantera»** en la ladera del volcán del mapa: las canteras de molinos de Gran Canaria están en laderas volcánicas de toba y basalto. El jugador debe **elegir la piedra adecuada** entre un canto rodado liso, una piedra volcánica con poros y obsidiana; cada opción explica por qué sirve o no. Solo la correcta da 2 bloques (una por muela), una vez por partida | game.js `quarry()`, `SCENES.mapa` (capa «Cantera») |
| **Molino de mano** fabricado por el jugador | Receta: piedra volcánica porosa ×2 + piedra basáltica ×1 como percutor (sale de «Recolectar»). Se fabrica con una **interacción de pulido**: cada golpe (clic, toque, Enter o Espacio) suma un 10 %, y mantener pulsado suma un 3 % cada 140 ms. Hay barra de progreso con `role="progressbar"`, tres fases con texto anunciado (`aria-live`: desbastar, dar forma circular a las dos muelas, abrir el agujero y alisar con arena y agua), golpe, polvo y el bloque que se transforma en molino. Sin animaciones con `prefers-reduced-motion` | game.js `polish()`; styles.css «interacción de pulido» |
| Fichas nuevas con fuente | «El molino de mano» (al pulir) y «El gofio» (al fabricarlo). El Cuaderno muestra enlaces a las fuentes: El Museo Canario, molino rotatorio inv. 3.313 (Gáldar); Rodríguez Rodríguez et al., «Las canteras de molinos de mano de Gran Canaria», *Tabona* 15; Cabildo de Gran Canaria, «La molienda de la vida» | game.js `fichas.molino`, `fichas.gofio`, `showJournal()` |
| Iconos nuevos | `assets/icon-cebada.png`, `icon-volcanica.png` e `icon-molino.png`, generados con la lámina como referencia de estilo, sin fondo blanco y compuestos sobre el mismo fondo oscuro con halo que las celdas de la lámina (celdas de 384×512, como las originales). También hay versiones `-transparente.png`. **No se modifica `resource-icons.png`**: la lectura 4×2 sigue intacta y los iconos nuevos se cargan como archivo aparte (`sprite-file`) | assets/; styles.css `.sprite-file` |
| Zurrón | 10 recursos en 5 columnas. El contador pasa a «x/10». Los objetos fabricados muestran el icono del molino y la etiqueta «(herramienta)» | game.js `inventory()`, `setHUD()`; index.html |

Prueba (1280×800 y 1920×1080): Almacén → cebada; Cantera → error con el canto rodado y acierto con la piedra porosa; Taller → Banot; intento de gofio sin molino (aviso); pulido con 4 clics, 2 Enter, 1 Espacio y mantener pulsado hasta el 100 %; gofio; ungüento. Resultado: el molino sigue en el zurrón después de hacer el gofio, se desbloquean las fichas molino y gofio, y hay 0 errores de consola y 0 peticiones de red. Capturas: `*_12b_almacen_cebada`, `*_12c/12d_cantera`, `*_13a…13d_pulir`, `*_13_taller`, `*_14_zurron`, `*_15_cuaderno`.
