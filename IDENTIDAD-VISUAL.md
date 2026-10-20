# Identidad visual de los anuncios

Guía para crear futuros HTML de este repositorio. Referencia: `index.html` (sesión 7), publicada en https://jdesales76.github.io/anuncios/. Actualizada el 20 de octubre de 2026.

## Criterios acordados

Mantener esta identidad salvo indicación expresa del usuario. Cambiar contenidos, fechas, número de sesión y enlaces según cada anuncio. No trasladar automáticamente los requisitos de una actividad a otra.

### Colores

| Uso | HEX |
| --- | --- |
| Amarillo principal | `#FDDA48` |
| Negro principal | `#0F1010` |
| Fondo blanco | `#FFFFFF` |
| Gris oscuro secundario | `#393836` |
| Texto auxiliar | `#676762` |
| Bordes | `#D9D9D3` |
| Tarjetas claras | `#F4F4F0` |
| Actividad práctica | `#FAFAF8` |

Los códigos son HEX, no referencias Pantone. Usar amarillo para la cabecera principal, etiquetas, iconos y acentos; negro para la franja de información y la tarjeta oscura. Texto negro sobre amarillo, blanco sobre negro y enlaces amarillos subrayados sobre negro.

### Tipografías

| Elemento | Fuente | Peso y tamaño de referencia |
| --- | --- | --- |
| Titular principal H1 | Anton | 400, `clamp(33px,5vw,62px)`, interlineado 1,1 |
| Encabezados H2 | Garet | 850, `clamp(25px,3vw,34px)`, interlineado 1,2 |
| Encabezados de tarjetas H3 | Garet | 850, 17px |
| Cabecera, etiquetas y entradillas de sección | Garet | 850, 11–12px, espaciado 0,13–0,15em |
| Fecha y lugar | Garet | 300, `clamp(15px,1.8vw,19px)` |
| Cuerpo de texto | Open Sans | 400; énfasis 700 |
| Subtítulo de cabecera | Open Sans | 16–20px, interlineado 1,55 |
| Introducción | Open Sans | 17–21px, interlineado 1,65 |
| Texto de tarjetas | Open Sans | 15px, interlineado 1,6 |

**Anton es la fuente confirmada del titular.** Usar su peso normal 400, sin negrita sintética. Su dibujo es naturalmente grueso: no sustituirla por Arial Narrow ni Impact para intentar aligerarla. Garet para encabezados y Open Sans para cuerpo son también elecciones explícitas del usuario.

Carga actual de fuentes:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Anton&family=Open+Sans:wght@400;600;700;800&display=swap">
<link rel="stylesheet" href="https://fonts.cdnfonts.com/css/garet">
```

Comprobar que las fuentes se descargan y se renderizan; declararlas en CSS no garantiza su carga. La hoja actual de Garet ofrece pesos 300 y 850. El número decorativo y el símbolo del anuncio original conservan Impact como recurso ornamental; no son la tipografía de titulares ni encabezados.

## Composición

Estética editorial, limpia, de alto contraste, con bloques rectangulares, bordes discretos y espacio generoso. Sin sombras ni esquinas redondeadas como recurso dominante.

1. Cabecera horizontal con asignatura/curso a la izquierda y etiqueta de sesión amarilla a la derecha; línea inferior negra de 2px.
2. Bloque principal amarillo con pequeña entradilla en mayúsculas, titular Anton y descripción breve. Número de sesión grande y tenue de fondo, opcional, sin competir con el texto.
3. Franja negra de fecha, horario y ubicación, con iconos lineales negros en cuadrados amarillos.
4. Introducción breve y bloque de actividad práctica claro, con banda lateral negra y símbolo amarillo.
5. Dos tarjetas paralelas: una clara y otra negra, con borde superior amarillo de 5px. Instrucciones, extensión y entrega, según la actividad.
6. Aviso breve de ancho completo cuando sea necesario.
7. Pie discreto con línea superior, asignatura/sesión y lema.

## Medidas y adaptación móvil

- Contenedor centrado: máximo 1080px; padding `28px clamp(14px,4vw,40px) 46px`.
- Cabecera amarilla: padding `clamp(24px,5vw,52px)`.
- Titular: ancho máximo 810px; descripción: 760px; introducción: 880px.
- Tarjetas: separación 16px y padding 23px.
- Separación antes del contenido: 36px; antes del aviso: 20px.
- A 650px o menos: franja de información y tarjetas pasan a una columna; padding exterior 12px 10px 25px y cabecera amarilla 28px 21px.
- Mantener legibilidad sin desbordamiento horizontal ni alturas fijas en los bloques de texto.

## Base CSS

```css
:root {
  --yellow: #FDDA48;
  --ink: #0F1010;
  --stone: #393836;
  --paper: #FFFFFF;
  --muted: #676762;
  --line: #D9D9D3;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  background: var(--paper);
  color: var(--ink);
  font-family: 'Open Sans', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
}
.hero h1 {
  font: 400 clamp(33px, 5vw, 62px)/1.1 'Anton', sans-serif;
  letter-spacing: .002em;
}
h2, h3, .topline, .kicker, .eyebrow {
  font-family: 'Garet', sans-serif;
  font-weight: 850;
}
```

## Contenido, accesibilidad y Canvas

- Español de España; mensajes breves, directos y fáciles de recorrer.
- Un único H1 y jerarquía clara de encabezados. Usar `lang="es"`, UTF-8 y viewport adaptable.
- Iconos decorativos con `aria-hidden="true"`; secciones y avisos con etiquetas accesibles.
- Enlaces descriptivos y subrayados. Enlaces a tareas de Canvas en nueva pestaña: `target="_blank" rel="noopener noreferrer"`, para salir del iframe.
- Respetar `prefers-reduced-motion`.
- La tipografía Times New Roman 12 mencionada en la actividad es un requisito de entrega del estudiante, no una fuente de esta web.
- Cada nuevo anuncio debe tener un archivo y URL propios; conservar los anteriores para que sus iframes no cambien de contenido.
- Publicación actual: GitHub Pages, rama `main`, raíz del repositorio.
- Incrustar la URL publicada por HTTPS en Canvas y ajustar la altura al contenido; 1500px es la referencia inicial, no una altura universal.

```html
<iframe
  src="URL_PUBLICADA_DEL_ANUNCIO"
  title="Título descriptivo del anuncio"
  width="100%"
  height="1500"
  style="border:0;"
  loading="lazy">
</iframe>
```

## Comprobación antes de entregar

Confirmar colores y carga real de las tres fuentes; revisar escritorio y móvil, ausencia de recortes, fecha y horario completos, enlaces y destino de entrega. Comprobar la publicación después del despliegue y facilitar el iframe de la URL correcta.
