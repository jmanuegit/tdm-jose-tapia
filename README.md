# 📘 Guía de Documentación — Proyecto Final
## Clases de Tenis de Mesa · Jose Tapia

---

## 1. ESTRUCTURA DE CARPETAS

```
tapia-ping-pong/
│
├── index.html            ← Página principal (Home)
├── historia.html         ← Historia del Tenis de Mesa
├── videos.html           ← Galería de Videos
├── materiales.html       ← Materiales y Recursos
├── jugadores.html        ← Campeones Olímpicos
│
├── css/
│   └── style.css         ← CSS compilado desde SCSS (listo para usar en el browser)
│
├── scss/
│   ├── _variables.scss   ← Colores, fuentes, espaciado, sombras, breakpoints
│   ├── _mixins.scss      ← Flexbox, media queries, tipografía, cards base
│   ├── _layout.scss      ← Header, hero, page-hero, section-title, footer
│   ├── _components.scss  ← Botones, info-card, video-card, champion-card, timeline
│   └── style.scss        ← Archivo raíz: importa todos los partials + animaciones
│
└── img/                  ← (Vacía — usa banderas de flagcdn.com vía URL)
```

> **Compilar SCSS a CSS:**
> ```bash
> sass scss/style.scss css/style.css --style=compressed --watch
> ```

---

## 2. DECISIONES DE DISEÑO

### 2.1 Paleta de Colores

| Variable SASS         | Color     | Uso                                      |
|-----------------------|-----------|------------------------------------------|
| `$color-primary`      | `#0d1b3e` | Fondo header, hero, cards oscuras        |
| `$color-accent`       | `#e63946` | CTA principal, bordes destacados, hover  |
| `$color-secondary`    | `#1d6fa4` | Links, botones secundarios, timeline     |
| `$color-gold`         | `#ffd60a` | Rankings, badges, pelota de ping pong    |
| `$color-light`        | `#f0f4f8` | Fondo secciones alternas                 |

**Justificación:** La paleta combina azul institucional (profesionalismo), rojo competencia (energía deportiva) y amarillo dorado (excelencia/campeonato). Transmite identidad de club deportivo de élite, diferenciándose de sitios genéricos.

### 2.2 Tipografía

- **Barlow Condensed** (display, headings): Fuente comprimida con peso 900, propia de carteles deportivos y uniformes. Da carácter fuerte y dinámico.
- **Nunito** (body): Redondeada y legible, equilibra la agresividad de los títulos con amabilidad en el cuerpo de texto.

### 2.3 Animaciones Implementadas

1. **`fadeInUp`** — Carga inicial del hero (título, subtítulo, botones)  
2. **`float`** — Pelota decorativa del hero flota suavemente  
3. **`pulse-border`** — Badges de ranking pulsan con un resplandor dorado  
4. **`slideInLeft`** — Entrada lateral para títulos de sección  

### 2.4 Componentes Clave SASS

**`@extend`** (herencia):
```scss
.section-title--white {
  @extend .section-title;   // hereda tipografía, tamaño y after
  color: $color-white;
  &::after { background: $color-gold; }
}
```

**Nesting (anidado):**
```scss
.champion-card {
  &:hover { transform: translateY(-10px); }
  &__avatar { ... }
  &__year { ... }
}
```

**Mixin con `@content`:**
```scss
@include respond-to('md') { font-size: 4.5rem; }
```

---

## 3. SEO IMPLEMENTADO

Cada página incluye:
- `<meta charset>`, `<meta viewport>`
- `<meta name="description">` — Único por página
- `<meta name="keywords">` — Términos relevantes
- `<title>` — Descriptivo con nombre del sitio
- `<meta property="og:*">` — Open Graph para redes sociales
- `alt=""` en todas las imágenes (`<img alt="Bandera de China">`)
- `aria-label` en links externos y botones
- `aria-labelledby` en secciones con heading asociado
- `loading="lazy"` en iframes y imágenes
- `rel="noopener noreferrer"` en todos los links externos

---

## 4. BOOTSTRAP Y RESPONSIVE DESIGN

### Grid utilizado:
```html
<div class="col-12 col-sm-6 col-lg-4">  <!-- Mobile → Tablet → Desktop -->
```

### Breakpoints aplicados:
- **xs** (< 576px): 1 columna, texto reducido, hero compacto
- **sm** (576px+): 2 columnas en cards
- **lg** (992px+): 3 columnas en grillas, hero título XL

### Personalización Bootstrap:
El sitio usa Bootstrap **solo para el grid**, sobreescribiendo todos los estilos de color, tipografía, botones y componentes con CSS propio. El resultado no parece una plantilla genérica.

---

## 5. PÁGINAS Y SU CONTENIDO

| Archivo          | Contenido principal                                         |
|------------------|-------------------------------------------------------------|
| `index.html`     | Hero, bio, tarjetas contacto, links rápidos                |
| `historia.html`  | Timeline 1880→hoy, datos curiosos                          |
| `videos.html`    | 4 iframes YouTube con cards responsive                     |
| `materiales.html`| 3 recursos externos + guía equipamiento básico             |
| `jugadores.html` | 10 campeones olímpicos (2008-2024) con filtro M/F          |

---

## 6. BIBLIOTECAS EXTERNAS (CDN)

| Biblioteca         | Versión  | Uso                                   |
|--------------------|----------|---------------------------------------|
| Bootstrap          | 5.3.3    | Grid responsive, navbar collapse      |
| Font Awesome       | 6.5.2    | Iconografía                           |
| AOS (Animate on Scroll) | 2.3.4 | Animaciones al hacer scroll        |
| Google Fonts       | —        | Barlow Condensed + Nunito             |

---

## 7. CHECKLIST FINAL DE ENTREGA

- [x] 5 archivos HTML completos y enlazados
- [x] SASS con partials: `_variables`, `_mixins`, `_layout`, `_components`, `style.scss`
- [x] Nesting, Extend y Animaciones en SASS
- [x] Bootstrap grid en todas las páginas
- [x] Mobile First (breakpoints min-width)
- [x] SEO: meta tags, alt, title, aria
- [x] HTML Semántico: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- [x] Links externos con `rel="noopener noreferrer"` y `target="_blank"`
- [x] Scroll-to-top funcional
- [x] Filtro JavaScript en jugadores.html
- [x] AOS en todas las páginas
- [x] Footer consistente en las 5 páginas
