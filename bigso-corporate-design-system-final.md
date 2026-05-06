# Bigso Design System — Nivel Corporativo

## Autoridad y Alcance

**Versión 2.0 · Mayo 2026**

Este documento es la fuente de verdad visual para las propiedades directas de Bigso:

| Propiedad | URL | Tipo |
|-----------|-----|------|
| Web corporativa | `bigso.co` | Marketing + institucional |
| SSO / Auth | `sso.bigso.co` | Autenticación centralizada |
| Admin interno | `admin.bigso.co` | Panel de gestión interno |
| Documentación | `docs.bigso.co` | Docs técnicas y APIs |

**Este sistema NO gobierna los productos del ecosistema** (ORDAMY, etc.). Cada producto tiene su propio DS que hereda la escala de espaciado, la font family y los principios — pero define su propia paleta y componentes específicos. Ver: *Apps by Bigso · Design System*.

### Relación con productos hijos

```
bigso-corporate-ds (este documento)
│
│  HERENCIA OBLIGATORIA para productos:
│  ├── Font family: Inter
│  ├── Escala de espaciado: base 4px
│  ├── Principios de accesibilidad (WCAG AA)
│  ├── Breakpoints y touch targets
│  └── Reduced motion support
│
│  PUEDE SOBREESCRIBIR cada producto:
│  ├── Paleta de colores
│  ├── Border radius preferences
│  ├── Shadow levels
│  └── Component-specific tokens
```

---

## 1. Identidad de Marca

### Logo

| Variante | Uso | Fondo |
|----------|-----|-------|
| Wordmark completo | Hero, navbar, materiales impresos | Claro |
| Wordmark invertido | Sobre fondos oscuros, footer | Oscuro |
| Isotipo (B) | Favicon, avatar, app icon, espacios reducidos | Cualquiera |
| Monochrome | Watermarks, co-branding discreto | Cualquiera |

### Área de respeto

Mínimo 1× la altura de la "B" del isotipo alrededor de cualquier variante del logo. Ningún elemento externo invade esta zona.

### Voz y tono corporativo

| Contexto | Tono | Ejemplo |
|----------|------|---------|
| Marketing (web) | Seguro, conciso, aspiracional. Sin tecnicismos. | "Soluciones digitales que escalan con tu negocio" |
| Legal (términos) | Preciso, formal, sin ambigüedad. | "Bigso S.A.S. ... conforme a la legislación vigente" |
| Documentación técnica | Claro, directo, con ejemplos. | "Endpoint: POST /api/v1/tenants — Crea un nuevo tenant" |
| Error messages | Humano, sin culpar, con acción clara. | "No pudimos conectar. Revisa tu red e intenta de nuevo." |

---

## 2. Sistema de Colores

### 2.1 Paleta Principal (Light Mode)

| Rol | Hex | Tailwind | Uso |
|-----|-----|----------|-----|
| **Primary** | `#4F46E5` | `indigo-600` | CTAs, enlaces, nav activa, focus rings |
| **Primary Hover** | `#4338CA` | `indigo-700` | Hover de elementos primarios |
| **Primary Light** | `#EEF2FF` | `indigo-50` | Fondos sutiles, badges, highlights |
| **Secondary** | `#64748B` | `slate-500` | Texto secundario, iconos inactivos |
| **Success** | `#10B981` | `emerald-500` | Confirmaciones, estados positivos |
| **Warning** | `#F59E0B` | `amber-500` | Alertas, atención requerida |
| **Error** | `#F43F5E` | `rose-500` | Errores, acciones destructivas |
| **Bg Primary** | `#FFFFFF` | `white` | Fondo de página |
| **Bg Secondary** | `#F8FAFC` | `slate-50` | Secciones alternas, cards sobre fondo |
| **Text Primary** | `#0F172A` | `slate-900` | Títulos, cuerpo principal |
| **Text Secondary** | `#475569` | `slate-600` | Subtítulos, descripciones |
| **Text Tertiary** | `#94A3B8` | `slate-400` | Placeholders, disabled, hints |
| **Border** | `#E2E8F0` | `slate-200` | Bordes de inputs, separadores, cards |
| **Border Hover** | `#CBD5E1` | `slate-300` | Hover en elementos con borde |

### 2.2 Paleta Dark Mode

| Rol | Hex | Tailwind |
|-----|-----|----------|
| Primary | `#818CF8` | `indigo-400` |
| Primary Hover | `#A5B4FC` | `indigo-300` |
| Bg Primary | `#020617` | `slate-950` |
| Bg Secondary | `#0F172A` | `slate-900` |
| Bg Tertiary | `#1E293B` | `slate-800` |
| Text Primary | `#F8FAFC` | `slate-50` |
| Text Secondary | `#94A3B8` | `slate-400` |
| Border | `#334155` | `slate-700` |

### 2.3 Estrategia de Dark Mode

- **Activación**: System preference por defecto + toggle manual persistido en `localStorage`.
- **Scope**: Todas las propiedades corporativas soportan dark mode.
- **Clase**: `class="dark"` en `<html>` (Tailwind darkMode: 'class').
- **Transición**: Cambio sin animación (instant) para evitar flash.

### 2.4 Reglas de uso del color

```
Primary (#4F46E5)      → SOLO para: CTAs, enlaces, active states, focus rings
                       → NUNCA para: fondos grandes, texto de cuerpo, bordes decorativos

Success (#10B981)      → SOLO para: estados completados, confirmaciones
                       → NUNCA para: CTAs genéricos, decoración

Error (#F43F5E)        → SOLO para: errores, acciones destructivas
                       → NUNCA para: elementos que no son errores

Warning (#F59E0B)      → SOLO para: alertas, info que requiere atención
                       → NUNCA para: decoración, estados normales
```

---

## 3. Tipografía

### Font Family

```css
--font-family: 'Inter', system-ui, -apple-system, sans-serif;
```

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

### Escala tipográfica

| Token | Size | Weight | Line Height | Letter Spacing | Tailwind | Uso |
|-------|------|--------|-------------|----------------|----------|-----|
| `display` | 48px | 700 | 1.1 | -0.02em | `text-5xl font-bold tracking-tight` | Hero único por página |
| `h1` | 36px | 700 | 1.2 | -0.02em | `text-4xl font-bold tracking-tight` | Título de página |
| `h2` | 30px | 600 | 1.25 | -0.01em | `text-3xl font-semibold` | Título de sección |
| `h3` | 24px | 600 | 1.3 | -0.01em | `text-2xl font-semibold` | Subtítulo de sección |
| `h4` | 20px | 600 | 1.4 | 0 | `text-xl font-semibold` | Título de card |
| `body-lg` | 18px | 400 | 1.6 | 0 | `text-lg` | Descripciones destacadas |
| `body` | 16px | 400 | 1.6 | 0 | `text-base` | Texto principal |
| `body-sm` | 14px | 400 | 1.5 | 0 | `text-sm` | Texto secundario, metadata |
| `caption` | 12px | 500 | 1.4 | 0.02em | `text-xs font-medium tracking-wider` | Labels, timestamps |
| `button` | 14px | 500 | 1 | 0.02em | `text-sm font-medium` | Texto de botones |

### Reglas tipográficas

- Un solo `display` por página (el hero).
- No saltar niveles de heading (h2 → h4 sin h3).
- `caption` solo para metadata y labels auxiliares, nunca para contenido principal.
- En mobile: `display` baja a 36px, `h1` a 30px. El resto se mantiene.

---

## 4. Espaciado

### Escala (base 4px)

| Token | rem | px | Uso típico |
|-------|-----|-----|-----------|
| `space-1` | 0.25 | 4 | Gap ícono-texto |
| `space-2` | 0.5 | 8 | Padding chips, gap inline |
| `space-3` | 0.75 | 12 | Padding inputs pequeños |
| `space-4` | 1 | 16 | Padding estándar botones/inputs |
| `space-5` | 1.25 | 20 | Gap entre elementos relacionados |
| `space-6` | 1.5 | 24 | Padding de cards, gap cards |
| `space-8` | 2 | 32 | Separación entre grupos |
| `space-10` | 2.5 | 40 | Separación entre secciones internas |
| `space-12` | 3 | 48 | Padding secciones hero |
| `space-16` | 4 | 64 | Separación entre secciones de página |
| `space-20` | 5 | 80 | Padding vertical secciones grandes |
| `space-24` | 6 | 96 | Separación máxima entre secciones |

### Contenedores

```html
<!-- Contenedor principal (max 1280px) -->
<div class="max-w-7xl mx-auto px-6 lg:px-8">

<!-- Contenedor estrecho para texto (max 768px) -->
<div class="max-w-3xl mx-auto px-6">
```

---

## 5. Sombras y Elevación

| Token | Valor | Tailwind | Uso |
|-------|-------|----------|-----|
| `shadow-xs` | `0 1px 2px 0 rgb(0 0 0 / 0.05)` | `shadow-xs` | Elementos casi planos |
| `shadow-sm` | `0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)` | `shadow-sm` | Cards default |
| `shadow-md` | `0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)` | `shadow-md` | Cards hover, dropdowns |
| `shadow-lg` | `0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)` | `shadow-lg` | Modales, tooltips |
| `shadow-xl` | `0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)` | `shadow-xl` | Notifications flotantes |

### Reglas de elevación

- Cards: `shadow-sm` → hover: `shadow-md` (transición 200ms)
- No usar sombra + borde grueso juntos (redundante)
- En dark mode: usar `shadow-black/20` y reducir intensidad
- Modales: siempre `shadow-lg` + overlay `bg-black/50`

---

## 6. Bordes y Radios

### Border Radius

| Token | Valor | Tailwind | Uso |
|-------|-------|----------|-----|
| `radius-sm` | 4px | `rounded-sm` | Chips, badges |
| `radius-md` | 6px | `rounded-md` | Inputs, botones, dropdowns |
| `radius-lg` | 8px | `rounded-lg` | Cards |
| `radius-xl` | 12px | `rounded-xl` | Cards de features, contenedores destacados |
| `radius-2xl` | 16px | `rounded-2xl` | Hero sections, imágenes grandes |
| `radius-full` | 9999px | `rounded-full` | Avatares, toggles, pills |

### Bordes

```css
/* Estándar */
border: 1px solid var(--color-border);      /* slate-200 */

/* Hover */
border-color: var(--color-border-hover);     /* slate-300 */

/* Focus */
border-color: var(--color-primary);          /* indigo-500 */
box-shadow: 0 0 0 2px var(--color-primary-light); /* ring */

/* Dark mode */
border-color: var(--color-border-dark);      /* slate-700 */
```

---

## 7. Componentes

### 7.1 Botones

#### Variantes

| Variante | Background | Text | Border | Uso |
|----------|-----------|------|--------|-----|
| **Primary** | `indigo-600` | `white` | ninguno | CTA principal. Uno por sección. |
| **Secondary** | `white` | `slate-700` | `slate-200` | Acciones secundarias |
| **Ghost** | `transparent` | `indigo-600` | ninguno | Acciones terciarias, inline |
| **Destructive** | `rose-500` | `white` | ninguno | Eliminar, cancelar irreversible |

#### Tamaños

| Tamaño | Padding | Font | Height mín. | Uso |
|--------|---------|------|-------------|-----|
| `sm` | `px-3 py-1.5` | 12px | 32px | Inline, tablas, badges |
| `md` | `px-4 py-2.5` | 14px | 40px | Default general |
| `lg` | `px-6 py-3` | 16px | 48px | CTAs hero, landing |

#### Estados

```html
<!-- Primary button con todos los estados -->
<button class="
  inline-flex items-center justify-center gap-2
  px-4 py-2.5
  bg-indigo-600 text-white text-sm font-medium
  rounded-md shadow-sm
  hover:bg-indigo-700
  active:bg-indigo-800
  focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-indigo-500 focus-visible:ring-offset-2
  disabled:opacity-50 disabled:cursor-not-allowed disabled:pointer-events-none
  transition-colors duration-150
">
  Texto del botón
</button>
```

#### Estado de carga

```html
<button class="... opacity-80 pointer-events-none" aria-busy="true">
  <svg class="animate-spin h-4 w-4" viewBox="0 0 24 24"><!-- spinner --></svg>
  Guardando...
</button>
```

### 7.2 Inputs

```html
<div class="w-full">
  <label for="email" class="block text-sm font-medium text-slate-700 dark:text-slate-300 mb-1.5">
    Correo electrónico
  </label>
  <input
    id="email"
    type="email"
    class="
      w-full px-3.5 py-2.5
      bg-white dark:bg-slate-900
      text-slate-900 dark:text-slate-50
      text-sm rounded-md
      border border-slate-200 dark:border-slate-700
      placeholder:text-slate-400
      focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-indigo-500/20 focus-visible:border-indigo-500
      disabled:bg-slate-50 disabled:text-slate-400 disabled:cursor-not-allowed
      transition-colors duration-150
    "
    placeholder="tu@empresa.com"
  >
  <p class="mt-1.5 text-xs text-slate-500">Texto de ayuda opcional</p>
</div>
```

#### Estado de error

```html
<input class="... border-rose-500 focus-visible:ring-rose-500/20" aria-invalid="true" aria-describedby="email-error">
<p id="email-error" class="mt-1.5 text-xs text-rose-500" role="alert">
  Ingresa un correo válido
</p>
```

**Specs:**
- Height: 40px
- Padding: 14px × 10px
- Radius: 6px
- Focus ring: 2px con 20% opacity del color
- Label siempre visible (no sustituir con placeholder)

### 7.3 Cards

```html
<div class="
  p-6
  bg-white dark:bg-slate-800/50
  rounded-lg
  border border-slate-200 dark:border-slate-700
  shadow-sm
  hover:shadow-md hover:border-slate-300 dark:hover:border-slate-600
  transition-all duration-200
">
  <h3 class="text-lg font-semibold text-slate-900 dark:text-slate-50">Título</h3>
  <p class="mt-2 text-sm text-slate-600 dark:text-slate-400">Descripción</p>
</div>
```

### 7.4 Badges

```html
<span class="inline-flex items-center px-2.5 py-0.5 text-xs font-medium rounded-full bg-indigo-50 text-indigo-700 dark:bg-indigo-500/10 dark:text-indigo-400">
  Badge
</span>
```

| Variante | Bg (light) | Text (light) | Bg (dark) | Text (dark) |
|----------|-----------|-------------|----------|------------|
| Default | `slate-100` | `slate-700` | `slate-700` | `slate-300` |
| Primary | `indigo-50` | `indigo-700` | `indigo-500/10` | `indigo-400` |
| Success | `emerald-50` | `emerald-700` | `emerald-500/10` | `emerald-400` |
| Warning | `amber-50` | `amber-700` | `amber-500/10` | `amber-400` |
| Error | `rose-50` | `rose-700` | `rose-500/10` | `rose-400` |

### 7.5 Header/Navbar

```html
<header class="sticky top-0 z-50 w-full bg-white/95 dark:bg-slate-900/95 backdrop-blur-sm border-b border-slate-200 dark:border-slate-700">
  <nav class="max-w-7xl mx-auto px-6 lg:px-8 h-16 flex items-center justify-between">
    <!-- Logo -->
    <a href="/" class="flex items-center gap-2">
      <span class="text-xl font-bold text-slate-900 dark:text-white">Bigso</span>
    </a>
    <!-- Nav links (hidden mobile) -->
    <div class="hidden md:flex items-center gap-8">
      <a class="text-sm font-medium text-slate-600 hover:text-indigo-600 dark:text-slate-400 dark:hover:text-indigo-400 transition-colors">Link</a>
    </div>
    <!-- CTAs -->
    <div class="flex items-center gap-3">
      <a class="text-sm font-medium text-slate-600 hover:text-indigo-600 transition-colors">Login</a>
      <a class="px-4 py-2 bg-indigo-600 text-white text-sm font-medium rounded-md hover:bg-indigo-700 transition-colors">Registrarse</a>
    </div>
  </nav>
</header>
```

- Altura: 64px (h-16)
- Backdrop blur para transparencia sutil en scroll
- Sticky top-0 z-50

### 7.6 Footer

```html
<footer class="w-full bg-slate-50 dark:bg-slate-900 border-t border-slate-200 dark:border-slate-800 py-12">
  <div class="max-w-7xl mx-auto px-6 lg:px-8">
    <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
      <div>
        <span class="text-lg font-bold text-slate-900 dark:text-white">Bigso</span>
        <p class="mt-3 text-sm text-slate-600 dark:text-slate-400">
          Ecosistema de soluciones digitales para empresas.
        </p>
      </div>
      <!-- Columnas de links -->
    </div>
    <div class="mt-8 pt-8 border-t border-slate-200 dark:border-slate-700 flex flex-col md:flex-row justify-between items-center gap-4">
      <p class="text-sm text-slate-500">© 2026 Bigso S.A.S. Todos los derechos reservados.</p>
    </div>
  </div>
</footer>
```

---

## 8. Iconografía

### Librería oficial: Heroicons

```bash
npm install @heroicons/react   # React
npm install @heroicons/vue     # Vue
```

O SVG directo desde https://heroicons.com

### Reglas

| Regla | Detalle |
|-------|---------|
| **Solo SVG** | Emojis como iconos de UI están prohibidos |
| **Outline por defecto** | Usar variante `outline` (stroke 1.5px) |
| **Solid para active** | Variante `solid` solo para estados activos (ej: nav selected) |
| **Color = currentColor** | Siempre heredar del texto padre |

### Tamaños por contexto

| Contexto | Tamaño | Clase |
|----------|--------|-------|
| Navbar / sidebar | 20px | `w-5 h-5` |
| Dentro de botones | 16px | `w-4 h-4` |
| Feature icons | 24px | `w-6 h-6` |
| Inline con texto | 16px | `w-4 h-4` |
| Decorativos grandes | 40-48px | `w-10 h-10` / `w-12 h-12` |

---

## 9. Animaciones y Transiciones

### Duraciones

| Token | Valor | Uso |
|-------|-------|-----|
| `duration-75` | 75ms | Micro-feedback (toggle) |
| `duration-150` | 150ms | Hover, color changes |
| `duration-200` | 200ms | Expand/collapse, state transitions |
| `duration-300` | 300ms | Modales, drawers |

### Easing

| Token | Valor | Uso |
|-------|-------|-----|
| `ease-out` | `cubic-bezier(0.0, 0, 0.2, 1)` | Entradas (elementos apareciendo) |
| `ease-in` | `cubic-bezier(0.4, 0, 1, 1)` | Salidas (elementos desapareciendo) |
| `ease-in-out` | `cubic-bezier(0.4, 0, 0.2, 1)` | Movimientos continuos |

### Reducción de movimiento

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### Prohibiciones

- Animaciones > 500ms para interacciones normales
- Layout shifts durante animaciones
- Animaciones que bloquean interacción (sin skip)
- Parallax agresivo que causa motion sickness

---

## 10. Layout y Responsive

### Breakpoints

| Token | Min Width | Tailwind | Uso |
|-------|-----------|----------|-----|
| Mobile | 0px | — | Mobile-first base |
| `sm` | 640px | `sm:` | Landscape phones |
| `md` | 768px | `md:` | Tablets |
| `lg` | 1024px | `lg:` | Desktop small |
| `xl` | 1280px | `xl:` | Desktop |
| `2xl` | 1536px | `2xl:` | Large screens |

### Grid patterns

| Patrón | Mobile | Tablet | Desktop | Gap |
|--------|--------|--------|---------|-----|
| Feature cards | 1 col | 2 cols | 3 cols | `gap-6` |
| Hero split | 1 col (stack) | 1 col | 2 cols | `gap-12` |
| Footer | 1 col | 2 cols | 4 cols | `gap-8` |
| Pricing | 1 col | 2 cols | 3 cols | `gap-8` |

### Touch targets

```
Mínimo absoluto:    44 × 44px para TODOS los elementos clickeables
Espaciado mínimo:   8px entre targets adyacentes
Botones nav mobile: 48px height mínimo
```

---

## 11. Estados del Sistema

### 11.1 Loading

| Tipo | Cuándo | Implementación |
|------|--------|----------------|
| **Skeleton** | Contenido de página cargando | Shapes con `animate-pulse bg-slate-200` |
| **Spinner** | Acciones puntuales (submit) | SVG spinner 16-20px con `animate-spin` |
| **Progress** | Procesos con % estimado | Barra horizontal con porcentaje |
| **Optimistic** | Acciones con alta probabilidad de éxito | UI actualiza inmediato, revierte si falla |

### 11.2 Empty states

```html
<div class="flex flex-col items-center justify-center py-12 text-center">
  <svg class="w-12 h-12 text-slate-300"><!-- Ilustración --></svg>
  <h3 class="mt-4 text-sm font-semibold text-slate-900">No hay elementos</h3>
  <p class="mt-1 text-sm text-slate-500">Comienza creando tu primer elemento.</p>
  <button class="mt-4 ...">Crear elemento</button>
</div>
```

Regla: Todo empty state tiene **descripción + acción**.

### 11.3 Error states

| Tipo | Posición | Ejemplo |
|------|----------|---------|
| Validación inline | Debajo del campo | "Ingresa un correo válido" |
| Toast/Notification | Top-right, z-50 | "Error al guardar. Intenta de nuevo." |
| Full page (500) | Centro de página | Ilustración + "Algo salió mal" + retry |
| Connection lost | Banner top, sticky | "Sin conexión. Reconectando..." |

---

## 12. Accesibilidad

### Contraste mínimo (WCAG 2.1 AA)

| Tipo | Ratio |
|------|-------|
| Texto normal (< 18px) | ≥ 4.5:1 |
| Texto grande (≥ 18px o ≥ 14px bold) | ≥ 3:1 |
| Componentes UI / gráficos | ≥ 3:1 |

### Focus management

```css
/* Focus visible — solo keyboard, no mouse */
:focus-visible {
  outline: 2px solid #4F46E5;
  outline-offset: 2px;
}

.dark :focus-visible {
  outline-color: #818CF8;
}

/* NUNCA hacer esto: */
:focus { outline: none; } /* ← PROHIBIDO sin reemplazo visible */
```

### ARIA patterns obligatorios

| Componente | ARIA requerido |
|-----------|----------------|
| Botón sin texto | `aria-label="Descripción"` |
| Input | `id` + `<label for>` (o `aria-label`) |
| Input con error | `aria-invalid="true"` + `aria-describedby` |
| Modal | `role="dialog"` + `aria-modal="true"` + `aria-labelledby` |
| Loading button | `aria-busy="true"` |
| Imágenes | `alt="Descripción"` (vacío solo si decorativa) |

### Navegación por teclado

| Tecla | Acción |
|-------|--------|
| `Tab` | Mover entre elementos focusables |
| `Enter` / `Space` | Activar elemento |
| `Escape` | Cerrar modal/dropdown/overlay |
| `Arrow keys` | Navegar dentro de menús, tabs, selects |

---

## 13. CSS Custom Properties

```css
:root {
  /* Colors */
  --color-primary: #4F46E5;
  --color-primary-hover: #4338CA;
  --color-primary-light: #EEF2FF;
  --color-secondary: #64748B;
  --color-success: #10B981;
  --color-warning: #F59E0B;
  --color-error: #F43F5E;
  --color-bg-primary: #FFFFFF;
  --color-bg-secondary: #F8FAFC;
  --color-text-primary: #0F172A;
  --color-text-secondary: #475569;
  --color-text-tertiary: #94A3B8;
  --color-border: #E2E8F0;
  --color-border-hover: #CBD5E1;

  /* Typography */
  --font-sans: 'Inter', system-ui, -apple-system, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* Spacing (base 4px) */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-20: 5rem;
  --space-24: 6rem;

  /* Radii */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 8px;
  --radius-xl: 12px;
  --radius-2xl: 16px;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-xs: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-sm: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);

  /* Transitions */
  --duration-fast: 150ms;
  --duration-normal: 200ms;
  --duration-slow: 300ms;
  --ease-default: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-out: cubic-bezier(0.0, 0, 0.2, 1);
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
}

/* Dark mode overrides */
@media (prefers-color-scheme: dark) {
  :root {
    --color-primary: #818CF8;
    --color-primary-hover: #A5B4FC;
    --color-primary-light: rgba(99, 102, 241, 0.1);
    --color-bg-primary: #020617;
    --color-bg-secondary: #0F172A;
    --color-text-primary: #F8FAFC;
    --color-text-secondary: #94A3B8;
    --color-text-tertiary: #64748B;
    --color-border: #334155;
    --color-border-hover: #475569;
  }
}
```

---

## 14. Checklist Pre-Delivery

### Visual

- [ ] Sin emojis como iconos (solo SVG)
- [ ] Contraste WCAG 4.5:1 verificado (light + dark)
- [ ] Touch targets ≥ 44×44px
- [ ] Hover states sin layout shift
- [ ] Transiciones 150–300ms
- [ ] Un solo botón primario por sección visible
- [ ] Tipografía solo en tamaños de la escala definida

### Funcional

- [ ] Focus visible en todos los interactivos
- [ ] Dark mode completo y funcional
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] Sin scroll horizontal en ningún breakpoint
- [ ] Loading states para toda carga asíncrona
- [ ] Empty states con acción
- [ ] Error states con mensaje útil + acción

### Accesibilidad

- [ ] Labels en todos los inputs
- [ ] `aria-label` en botones sin texto
- [ ] `alt` en imágenes significativas
- [ ] Navegación completa por teclado
- [ ] `prefers-reduced-motion` respetado
- [ ] Skip-to-content link en páginas largas

---

*Documento mantenido por el equipo de diseño de Bigso · v2.0 · Mayo 2026*
