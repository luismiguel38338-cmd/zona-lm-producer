# ZONA LM PRODUCER — Productor de música en el teléfono

App web en un solo archivo, sin CDN, en español. Diseño negro/violeta, marca Zona LM Shot.

## Archivos
- `index.html` — toda la app (HTML + CSS + JS, 22.940 bytes)

## Qué funciona (verificado)
- Sonido real con WebAudio: pads sintetizados (kick, snare, hi-hat, güira, tambora, conga, palma, platillo, bajo) — osciladores + ruido, no son botones decorativos.
- Loops base reales por género: dembow, merengue típico, bachata, reguetón (patrones de 16 pasos distintos).
- Secuenciador de 16 pasos × 6 pistas, editable tocando los cuadros.
- Tempo BPM 60–180, volumen maestro.
- Piano (8 teclas blancas + 5 negras) y 6 acordes (Am, C, G, F, Dm, Em), 4 instrumentos.
- Efectos: eco (delay) y reverberación (convolver con impulso generado), ecualizador de 3 bandas (graves/medios/agudos).
- Subir voz/audio propio (MP3/WAV, decodeAudioData), reproducir en loop con volumen propio, mezclado con el beat.
- Guardar/cargar/listar beats en localStorage (`zonalm_producer_projects`).
- Grabar en vivo con MediaRecorder (descarga WebM) y exportar WAV real con OfflineAudioContext (4 compases del patrón actual, PCM 16-bit estéreo).

## Verificación hecha (2026-11-27)
- `node --check` del JS extraído: OK, sin errores de sintaxis.
- Servidor local Python: `GET /index.html` → HTTP 200, 22.940 bytes.
- Sin CDN: no hay enlaces externos en el HTML.
- NO probado en un teléfono real ni en un navegador real: el sonido WebAudio, la grabación y la exportación WAV se verificaron solo por código y sintaxis, no con una sesión de audio real. El usuario debe tocar “ENCENDER ESTUDIO” primero (los navegadores bloquean el audio hasta un gesto).

## Cómo publicarlo en Vercel
Opción A (Drop, como Chipeo RP): subir solo `index.html` a Vercel Drop como proyecto nuevo, p. ej. `zona-lm-producer` → https://zona-lm-producer.vercel.app/
Opción B (Git): crear el repositorio en GitHub (el formulario ya está abierto en el navegador del usuario), subir `index.html` + este README, conectar el repo en Vercel.

## Qué falta / límites honestos
- No hay sonidos grabados reales (samples): todo es síntesis WebAudio. Suena bien para dembow/merengue, pero no es un sample de tambora real.
- La grabación en vivo descarga WebM (no WAV); el WAV solo exporta el patrón del secuenciador, no la voz subida ni el piano tocado a mano.
- Los proyectos guardados viven solo en ese teléfono/navegador (localStorage), no se sincronizan.
- No hay cuenta, ni nube, ni tienda: es una app local.
