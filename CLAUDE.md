# Portfolio - Contexto de desarrollo

## Resumen
Portfolio single-file HTML para Victor Garcia (victoormga.github.io). Nivel Awwwards con GSAP, Three.js, animaciones avanzadas. Desplegado en GitHub Pages.

## Stack
- HTML/CSS/JS en un solo archivo (`index.html`)
- **GSAP + ScrollTrigger**: animaciones de entrada (hero, char split, section reveals)
- **Three.js**: torus knot wireframe en hero (position fixed, fade out on scroll)
- **IntersectionObserver**: reveal de secciones (reemplaza gsap.from que causaba bugs)
- Fuentes: Syne (titulos), Inter (body), JetBrains Mono (labels/code)
- CSS custom properties para dark/light theme
- Compatible con `file://` (var en vez de const, try/catch localStorage, HTML entities)

## Estructura de secciones
1. **Nav**: fixed, transparente en top, blur al scrollear, se oculta al bajar y reaparece al subir
2. **Hero**: nombre "Victor Garcia" con hover swap a "Full Stack Dev." (opacity transition 1.5s), badge, subtitulo word-by-word, CTAs
3. **About**: grid 2 columnas (texto + stats cards con glow effect)
4. **Tecnologias**: marquee horizontal con loop infinito + titulo
5. **Experiencia**: timeline items (Pisamonas, Samana Digital) + education cards
6. **Contacto**: links a email, LinkedIn, GitHub
7. **Footer**

## Efectos implementados
- Custom cursor con mix-blend-mode: difference
- Noise/grain SVG overlay
- Glow/spotlight cards (radial-gradient sigue el mouse)
- Char split en titulos de seccion (hover colorea chars con delay)
- Hero title hover swap (Victor Garcia <-> Full Stack Dev.)
- Three.js torus knot parallax + fade out al scrollear
- Nav auto-hide on scroll down, show on scroll up

## Problemas resueltos (no repetir)
- **Lenis**: ELIMINADO. Rompia el scroll completamente. No volver a usar.
- **gsap.from con ScrollTrigger para content visibility**: peligroso, si el trigger no dispara el contenido queda invisible para siempre. Usar IntersectionObserver con CSS transitions en su lugar.
- **Hero hover text swap con overflow:hidden/clip-path**: no funciona. La solucion que funciona es opacity swap con dos contenedores superpuestos (title-default + title-hover).
- **Section title char split come espacios**: display:inline-block colapsa espacios. Fix: innerHTML='&nbsp;' con width:0.3em para chars de espacio.
- **Descenders cortados en titulos (g, p, y)**: line-height:1.4 + overflow:visible + vertical-align:bottom en .char spans.
- **Mobile hamburger z-index**: overlay a z-index:9999, hamburger button a 10000.
- **File revert accidental**: el commit 5835ea3 tiene la version Awwwards buena.

## Preferencias del usuario
- Sin emojis en la UI
- Sin labels "//" en secciones
- Spacing moderado entre secciones (8rem desktop, 5rem mobile)
- Nav sin border-bottom, fundido con el fondo
- Three.js shape no debe interferir con contenido al scrollear
- Transiciones suaves (1.5s para hero swap)
- Nombre de seccion skills: "Tecnologias" (no "Herramientas que uso")
- Sin tarjetas de skill groups (Backend/Frontend/DevOps) - solo marquee
