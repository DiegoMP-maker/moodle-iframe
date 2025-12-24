# moodle-iframe

Integraciones en Moodle con HTML autocontenido.

## Estructura

- `lessons/<unidad>/index.html`: actividades publicables en Vercel.
- `templates/iframe-base.html`: plantilla base con estilos comunes y slots.
- `assets/images/`: imágenes compartidas (mantén formatos optimizados).
- `assets/videos/`: vídeos compartidos (versiones web y streaming).

## Rutas en Vercel

Cada actividad se accede por la ruta de su carpeta, por ejemplo:

- `/lessons/b2-turismo/`

La configuración de rutas está en `vercel.json`.

## Ejemplo de iframe para Moodle

Usa un `<iframe>` con atributos accesibles y de carga diferida:

```html
<iframe
  title="Actividad: Turismo B2"
  src="https://<tu-proyecto>.vercel.app/lessons/b2-turismo/"
  width="100%"
  height="720"
  loading="lazy"
  allowfullscreen
></iframe>
```

## Recomendaciones de tamaño y ajustes en Moodle

- Inserta el iframe en un recurso tipo **“Área de texto y medios”**.
- Cambia al **modo HTML** para pegar el código sin que Moodle lo modifique.
- Usa `width="100%"` para que el contenido sea responsive.
- Ajusta `height` según la altura real de la actividad (p. ej., 640–900 px).

## Cómo localizar la URL desplegada en Vercel por lección

1. Abre el proyecto en Vercel y entra al último deploy en **Deployments**.
2. Copia el dominio del deploy (por ejemplo, `https://<tu-proyecto>.vercel.app`).
3. Añade la ruta de la lección según su carpeta en `lessons/`:
   - `lessons/b2-turismo/index.html` → `https://<tu-proyecto>.vercel.app/lessons/b2-turismo/`
4. Usa esa URL en el `src` del iframe.

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

## Recomendaciones de medios (imágenes y vídeo)

- **Imágenes**: usa WebP o AVIF para menor peso y buena calidad. Mantén una versión JPEG/PNG solo si necesitas máxima compatibilidad.
- **Vídeo**: prioriza MP4 (H.264) y, si aplica, provee HLS para streaming adaptativo.
- **`poster`**: define un `poster` en `<video>` para mostrar una portada ligera antes de reproducir.
- **`controls`**: habilita `controls` en vídeos para que el alumnado controle la reproducción.
- **Evita `autoplay` en iframes de Moodle**: Moodle y los navegadores suelen bloquearlo; además mejora accesibilidad y rendimiento.
