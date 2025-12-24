# moodle-iframe

Integraciones en Moodle con HTML autocontenido.

## Estructura

- `lessons/<unidad>/index.html`: actividades publicables en Vercel.
- `templates/iframe-base.html`: plantilla base con estilos comunes y slots.

## Rutas en Vercel

Cada actividad se accede por la ruta de su carpeta, por ejemplo:

- `/lessons/b2-turismo/`

La configuración de rutas está en `vercel.json`.

## Clonar la plantilla para nuevas actividades

1. Copia `templates/iframe-base.html` a una nueva carpeta, por ejemplo:
   - `lessons/b2-nueva-unidad/index.html`
2. Rellena los slots:
   - `<!-- SLOT: title -->`: título del documento.
   - `<!-- SLOT: additional-styles -->`: estilos específicos de la actividad.
   - `<!-- SLOT: content -->`: HTML del contenido principal.
   - `<!-- SLOT: scripts -->`: scripts opcionales (evita dependencias externas si se embebe en Moodle).
3. Publica la actividad con su nueva ruta, por ejemplo:
   - `/lessons/b2-nueva-unidad/`
