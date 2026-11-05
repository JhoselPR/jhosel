# Portfolio · Jhosel Ruiz

Portfolio personal de Félix Jhosel Peñaloza Ruiz, desarrollador frontend. Reúne experiencia, proyectos destacados con video de demostración y CV descargable, en español e inglés.

## Stack

- React 19 y Vite
- Tailwind CSS 4
- Framer Motion para las animaciones
- i18next y react-i18next para el cambio de idioma
- react-icons

## Desarrollo

Requiere Node.js y pnpm.

```bash
pnpm install
```

```bash
pnpm dev
```

| Comando | Uso |
|---|---|
| `pnpm dev` | Servidor de desarrollo |
| `pnpm build` | Genera la versión de producción en `dist` |
| `pnpm preview` | Sirve la versión compilada |
| `pnpm lint` | Revisa el código con ESLint |

## Estructura

| Carpeta | Contenido |
|---|---|
| `src/sections` | Secciones de la página: inicio, sobre mí, experiencia, proyectos y contacto |
| `src/components` | Navbar, tarjetas de proyecto, video de demostración y demás piezas reutilizables |
| `src/data` | Orden de los proyectos y de la experiencia |
| `src/i18n` | Todos los textos en `es.json` y `en.json`, más la configuración de idiomas |
| `src/utils` | Script que genera el retrato en ASCII de la portada |
| `public/img` | Capturas, videos e imágenes de los proyectos |
| `public/files` | CV en español e inglés |

## Contenido

Casi todo el contenido vive en `src/i18n/es.json` y `src/i18n/en.json`. Cada cambio de texto va en ambos archivos.

### Añadir un proyecto

1. Agrega su clave en `src/data/projects.js`, en la posición donde debe aparecer. Con `featured: true` se muestra como destacado. Sin él, va a "Otros proyectos".
2. Agrega sus textos en `projects.items.<clave>` de ambos archivos de idioma: `label`, `title`, `context`, `description`, `stack`, `code`, `deploy` e `img`. Los destacados llevan además `highlight`.
3. Guarda su imagen en `public/img/project-card`.

Campos opcionales:

- `video` y `videoAspect`: video de demostración que se reproduce al pasar el cursor sobre la captura. `videoAspect` es la proporción del video, por ejemplo `"1280 / 802"`.
- `award`: distintivo con trofeo en las tarjetas de "Otros proyectos".
- `download`: cambia el enlace de demo por uno de descarga.

### Videos de demostración

Los videos van en MP4 (H.264), sin audio, a unos 1280 px de ancho y con pocos megas. Un video sin comprimir hace pesado el repositorio y la página.

### Experiencia

El orden está en `src/data/experience.js` y el contenido en `experience.items` de cada archivo de idioma.

### CV

Los PDF están en `public/files`. La ruta de cada idioma se define en `cvFile` dentro de su archivo de idioma, así que el enlace abre el CV del idioma activo.

### Retrato ASCII

El retrato de la portada se genera desde `src/utils/input.png`. Para regenerarlo después de cambiar la imagen:

```bash
cd src/utils && node processImage.js
```

El script escribe `asciiData.js` con tres tamaños del retrato.
