# Apps by Bigso · Sistema de Diseño para Productos

## Autoridad y Alcance

**Versión 4.0 · Mayo 2026**

Este documento gobierna la experiencia de diseño de **todos los productos SaaS multi-tenant** que operan bajo el ecosistema Bigso (ORDAMY, y futuros productos). Define la arquitectura de co-branding, los tokens de diseño por rol, y las reglas absolutas que cada producto debe cumplir.

### Qué hereda del DS corporativo de Bigso

| Herencia obligatoria | Puede sobreescribir |
|---------------------|---------------------|
| Font family: Inter | Paleta de colores (definir propia) |
| Escala de espaciado (base 4px) | Border radius preferences |
| Principios WCAG AA | Niveles de sombra |
| Breakpoints (sm/md/lg/xl/2xl) | Iconografía (set específico) |
| Touch targets (44×44px mín.) | Componentes específicos de producto |
| Reduced motion support | Tono de voz del producto |
| Heroicons como set base de iconos | — |

### Para quién es este documento

- Diseñadores creando interfaces de productos Bigso
- Desarrolladores implementando dashboards multi-tenant
- Product managers validando pantallas antes de entrega

---

## 1. Arquitectura de Marca

### Jerarquía de tres niveles

```
BIGSO (holding)
  └── PRODUCTO (app SaaS: ORDAMY, etc.)
        └── TENANT (negocio del cliente final)
```

| Nivel | Rol | Voz | Aparece en |
|-------|-----|-----|-----------|
| **Holding** | Respaldo legal. Nunca protagoniza. | Institucional, formal | Footer legal, TyC, facturación |
| **Producto** | La marca que el mercado compra. | Empoderador, directo | Landing, onboarding, watermark, login |
| **Tenant** | El negocio del usuario final. Controla su espacio. | Personal, práctico | Dashboard, login contextual, subdominios |

### Regla de oro

> Cuanto más profundo está el usuario dentro del producto, más retrocede la marca del producto y más avanza la marca del tenant.

### Presencia por pantalla

| Pantalla | Tenant | Producto | Holding |
|----------|--------|----------|---------|
| **Landing pública** | Ausente | ★★★ Protagonista | Solo nav + footer legal |
| **Login contextual** | ★★★ Protagonista | Sello secundario | Invisible |
| **Onboarding** | Ausente (en creación) | ★★ Principal | Solo en TyC |
| **Dashboard interno** | ★★★ Protagonista | Watermark mínimo | Invisible |
| **Emails transaccionales** | Remitente | Footer discreto | No aparece |
| **PDFs generados** | Header principal | Pie de página | No aparece |

### Distribución de atención visual

Cuando conviven múltiples marcas:
- **Protagonista**: ~70% (tamaño, color, posición superior)
- **Secundario**: ~25%
- **Terciario**: ~5% (solo para quien busca)

---

## 2. Paleta de Colores

### Filosofía

Este sistema define **roles y tokens**, no colores fijos. Cada producto implementa su propia paleta respetando la estructura. Los valores hexadecimales que aparecen son ejemplos.

### 2.1 Tokens de marca del producto

| Token | Rol | Ejemplo ORDAMY | Uso |
|-------|-----|----------------|-----|
| `--brand-dark` | Primario oscuro | `#1a1a2e` | Sidebars, navbars, tipografía de peso |
| `--brand-action` | Color de acción | `#e05a20` | CTAs, highlights, active states |
| `--brand-bg` | Fondo público cálido | `#fdf6ef` | Landing hero, secciones de marketing |

**Regla inviolable**: `--brand-action` es EXCLUSIVO para acciones positivas y CTAs. Nunca para errores, warnings o estados negativos.

### 2.2 Tokens neutros

| Token | Rol | Contraste | Ejemplo |
|-------|-----|-----------|---------|
| `--text-primary` | Títulos y cuerpo | Máximo · WCAG AA+ | `#1a1a2e` |
| `--text-secondary` | Labels, metadata | Medio · WCAG AA | `#6b6b80` |
| `--text-muted` | Apoyo, hints | Bajo · WCAG AA mín. | `#9a9a9a` |
| `--text-hint` | Watermarks, legal | Decorativo | `#bdbdbd` |
| `--surface` | Cards, modales | — | `#ffffff` |
| `--surface-soft` | Fondo de secciones | — | `#f4f2ee` |
| `--border` | Bordes principales | — | `#e5ddd4` |
| `--border-light` | Divisores internos | — | `#f0f0f0` |

### 2.3 Tokens semánticos

Cada estado tiene **texto oscuro + fondo pastel** para cumplir contraste:

| Estado | Token texto | Token bg | Uso |
|--------|------------|----------|-----|
| Éxito | `--success` | `--success-bg` | Completado, confirmado |
| Advertencia | `--warning` | `--warning-bg` | Pendiente, atención |
| Error | `--danger` | `--danger-bg` | Cancelado, fallido |
| Info | `--info` | `--info-bg` | Neutral informativo |

Los colores semánticos son **absolutos**: no cambian por tenant, por producto, ni por contexto.

### 2.4 Token del tenant

```css
/* Modo estándar: hereda del producto */
--tenant-accent: var(--brand-action);

/* Modo white-label: definido por el tenant */
--tenant-accent: #2563eb; /* ejemplo: azul corporativo del tenant */
```

**Dónde aplica `--tenant-accent`:**
```css
.btn-primary-tenant  { background: var(--tenant-accent); }
.metric-value        { color: var(--tenant-accent); }
.tenant-avatar       { background: var(--tenant-accent); }
.nav-item.active     { border-left-color: var(--tenant-accent); }
```

**Dónde NUNCA aplica:**
- Badges de estado (usan semánticos)
- Mensajes de error
- Textos de cuerpo

### 2.5 Validación de color del tenant

Antes de aceptar un color personalizado de tenant:

```
✓ Texto blanco sobre el color: ratio ≥ 4.5:1
✓ El color sobre --surface: ratio ≥ 3:1
✓ Distinguible de --danger (no usar rojos puros)
✓ Distinguible de --success (no usar verdes puros)
```

Si el color del tenant no pasa validación → usar `--brand-action` como fallback.

### 2.6 Dark Mode (productos)

Cada producto decide si soporta dark mode. Si lo implementa:

| Token | Light | Dark |
|-------|-------|------|
| `--surface` | `#ffffff` | `#1e1e2e` |
| `--surface-soft` | `#f4f2ee` | `#0f0f1a` |
| `--text-primary` | `#1a1a2e` | `#f5f5f5` |
| `--border` | `#e5ddd4` | `#2a2a3e` |

Regla: El sidebar siempre usa `--brand-dark` (sin cambio en dark mode ya que es inherentemente oscuro).

---

## 3. Tipografía

### Font

```css
--font-sans: 'Inter', system-ui, -apple-system, sans-serif;
--font-mono: 'JetBrains Mono', monospace;
```

### Escala por rol

| Rol | Size | Weight | L-H | L-S | Uso |
|-----|------|--------|-----|-----|-----|
| Hero | 28–32px | 800 | 1.1 | -0.5px | Un título por landing. Máximo impacto. |
| H2 Section | 20–22px | 700 | 1.25 | -0.3px | Títulos de sección |
| H3 Card | 16–18px | 600 | 1.3 | 0 | Títulos de cards y widgets |
| Body | 14px | 400 | 1.6 | 0 | Contenido principal |
| Body Small | 13px | 400 | 1.5 | 0 | Texto en tablas, UI densa |
| Label | 11–12px | 500–600 | 1.4 | 0.04em | Labels de campo (uppercase) |
| Micro | 10px | 400 | 1.3 | 0.02em | Watermarks, "powered by" |
| Caption | 9px | 400–500 | 1.2 | 0.04em | Plan del tenant, metadata mínima |

### Colores de texto

| Rol | Token | Aplicación |
|-----|-------|-----------|
| Primary | `--text-primary` | Títulos y contenido principal |
| Secondary | `--text-secondary` | Labels, metadata, subtítulos |
| Muted | `--text-muted` | Texto de apoyo, hints |
| Hint | `--text-hint` | Watermarks, legal, "powered by" |
| Accent | `--brand-action` | Solo énfasis de marca intencional |
| Error | `--danger` | Mensajes de error de validación |

### Reglas tipográficas

| ✓ Hacer | ✗ No hacer |
|---------|-----------|
| Un solo typeface en la UI operativa | Mezclar más de 2 fonts |
| Mínimo absoluto: 9px (solo caption) | Texto < 9px en ningún contexto |
| Color accent solo para links/énfasis | Accent en texto de cuerpo sin propósito |
| Uppercase + tracking en labels | Uppercase en texto de cuerpo |

---

## 4. Espaciado y Radios

### Escala de espaciado (base 4px)

| px | Uso |
|----|-----|
| 4 | Gap ícono-texto |
| 8 | Gap entre badges, chips |
| 12 | Padding interno cards pequeñas (métricas) |
| 16 | Padding estándar de cards y botones |
| 20 | Gap entre items de nav |
| 24 | Padding cards principales |
| 32 | Separación entre grupos |
| 40 | Padding de hero sections |
| 64 | Separación entre secciones de landing |

### Radios de borde

| Componente | Radius | Token |
|-----------|--------|-------|
| Badges (pill) | 20px | `--radius-pill` |
| Botones | 8px | `--radius-btn` |
| Inputs | 7px | `--radius-input` |
| Cards métricas | 8px | `--radius-sm` |
| Cards principales | 10–14px | `--radius-md` / `--radius-lg` |
| Modales | 14px | `--radius-lg` |
| Avatar sidebar | 7px | — |
| Avatar login | 12px | — |
| Avatar usuario (topbar) | 50% | `rounded-full` |

### Bordes

| Contexto | Grosor |
|----------|--------|
| Estándar (cards, inputs, dividers) | 0.5px / 1px |
| Botón outline activo | 1.5px |
| Nav item active (border-left) | 2px |

### Sombras

| Token | Valor | Uso |
|-------|-------|-----|
| `--shadow-card` | `0 1px 3px rgba(0,0,0,0.07), 0 4px 12px rgba(0,0,0,0.04)` | Cards en reposo |
| `--shadow-elevated` | `0 4px 16px rgba(0,0,0,0.10), 0 1px 4px rgba(0,0,0,0.06)` | Cards hover, modales, login card |

---

## 5. Co-branding por Pantalla

### 5.1 Navbar de landing pública

**Layout:**
```
[ PRODUCTO | by BIGSO ]              [ Login ] [ CTA primario ]
```

| Elemento | Spec |
|----------|------|
| Logo del producto | 15–17px · weight 800 · `--brand-dark` · letter-spacing: -0.5px |
| Separador | `|` en `--border-light` |
| "by BIGSO" | 10px · `--text-muted` · letter-spacing: 0.04em |
| Navbar height | 44–52px |
| Fondo | `--surface` + `border-bottom: 0.5px solid --border` |
| CTA | Botón primary con `--brand-action` |
| Login link | Ghost/text, `--text-secondary` |

### 5.2 Login contextual del tenant

```
┌──────────────────────────────────┐
│                                  │
│      [ Avatar 52×52 ]            │
│      Nombre del Tenant           │
│      slug.producto.co            │
│                                  │
│      ┌────────────────────┐      │
│      │ Email              │      │
│      └────────────────────┘      │
│      ┌────────────────────┐      │
│      │ Contraseña         │      │
│      └────────────────────┘      │
│      ┌────────────────────┐      │
│      │    Ingresar        │      │
│      └────────────────────┘      │
│                                  │
│  ──────────────────────────────  │
│  Plataforma gestionada por       │
│  PRODUCTO                        │
│  un producto de BIGSO            │
│                                  │
└──────────────────────────────────┘
```

| Elemento | Spec |
|----------|------|
| Avatar tenant | 52×52px · radius 12px · bg `--tenant-accent` · iniciales blancas 18px/800 |
| Nombre tenant | 16px · 700 · `--text-primary` · centrado |
| URL subdominio | 11px · `--text-muted` · centrado |
| Card | padding 28px · radius 14px · `--shadow-elevated` |
| "gestionada por PRODUCTO" | 10px · `--text-hint` · nombre en 700 |
| "un producto de BIGSO" | 10px · `--text-hint` · casi invisible |
| Botón ingresar | Full-width · `--tenant-accent` · white text |

### 5.3 Sidebar del dashboard

```
┌──────────────────┐
│ [Av] Tenant Name │  ← Header: logo/avatar + nombre + plan
│      Plan Pro    │
├──────────────────┤
│ ▸ Dashboard      │  ← Nav items con iconos SVG
│   Órdenes       │
│   Menú          │
│   Reportes      │
│   Config        │
├──────────────────┤
│ powered by       │  ← Footer: watermark mínimo
│ PRODUCTO         │
└──────────────────┘
```

| Elemento | Spec |
|----------|------|
| Ancho | 180–220px |
| Fondo | `--brand-dark` |
| Avatar tenant | 30×30px · radius 7px · bg `--tenant-accent` · iniciales 11px/700 |
| Nombre tenant | 12px · 600 · white |
| Plan | 9px · rgba(255,255,255, 0.35) |
| Nav item default | 13px · 400 · rgba(255,255,255, 0.55) · padding 8px 16px |
| Nav item hover | rgba(255,255,255, 0.7) · bg rgba(255,255,255, 0.05) |
| Nav item active | white · border-left: 2px `--tenant-accent` · bg rgba(255,255,255, 0.07) |
| Nav icons | 18px · outline · currentColor |
| "powered by" | 9px · rgba(255,255,255, 0.2) · bottom fixed |
| **Holding aquí** | **NO APARECE** |

### 5.4 Topbar del dashboard

```
[ Buenos días, Tenant Name 👋 ]        [ Badge alertas ] [ Avatar usuario ]
```

| ✓ Incluir | ✗ No incluir |
|-----------|-------------|
| Saludo con nombre del tenant | Logo del producto |
| Badge de pendientes/alertas | Nombre del holding |
| Avatar del usuario + menú | Navegación (va en sidebar) |
| Breadcrumbs (si aplica) | Buscar (ir en sidebar o contenido) |

| Spec | Valor |
|------|-------|
| Height | 44–52px |
| Fondo | `--surface` |
| Border | `border-bottom: 0.5px --border-light` |
| Saludo | 13–14px · 600 · `--text-primary` |
| Avatar usuario | 28–32px · `rounded-full` |

### 5.5 Sellos "Powered by"

| Contexto | Formato | Spec |
|----------|---------|------|
| Sidebar oscuro | `powered by PRODUCTO` | 9px · rgba(255,255,255, 0.2) · solo texto |
| Login card | `Plataforma gestionada por PRODUCTO` | 10px · `--text-hint` · nombre en bold |
| Emails | Logo pequeño de producto en footer | 24px height max · gris |
| PDFs | `Generado por PRODUCTO · bigso.co` | 8px · gris · margen inferior del doc |
| **En TODOS los contextos** | `"powered by PRODUCTO"` | **NUNCA "powered by BIGSO"** |

---

## 6. Botones

### Variantes

| Variante | Background | Color | Border | Cuándo |
|----------|-----------|-------|--------|--------|
| **Primary** | `--tenant-accent` | white | — | CTA principal. Solo uno visible por pantalla. |
| **Outline** | transparent | `--brand-action` | 1.5px `--brand-action` | Acciones secundarias importantes |
| **Ghost** | transparent | `--text-secondary` | 0.5px `--border` | Acciones terciarias |
| **Destructive** | `--danger-bg` | `--danger` | 0.5px lighter | Eliminar, cancelar irreversible |

### Tamaños

| Size | Padding | Font | Height |
|------|---------|------|--------|
| `sm` | 6px 14px | 12px | 32px |
| `md` | 10px 22px | 13px | 40px |
| `lg` | 13px 28px | 15px | 48px |

### Constantes

```css
border-radius: 8px;
font-weight: 600;
transition: all 150ms ease-out;
```

### Estados

| Estado | Efecto visual |
|--------|--------------|
| Default | Base |
| Hover | Background 10–15% más oscuro · cursor: pointer |
| Active | Background 20% más oscuro · opcional: translateY(1px) |
| Focus | `box-shadow: 0 0 0 3px rgba(accent, 0.15)` · `outline: none` |
| Disabled | `opacity: 0.5` · `cursor: not-allowed` · `pointer-events: none` |
| Loading | Spinner SVG 16px + texto "Guardando..." · disabled |

---

## 7. Formularios

### Estructura de campo

```
LABEL (uppercase)         ← 11px · 600 · --text-secondary · 0.04em tracking
┌─────────────────────┐
│ Placeholder text     │  ← 13px · 400 · --text-hint
└─────────────────────┘
Mensaje de ayuda/error   ← 11px · --text-muted (o --danger)
```

### Specs del input

| Propiedad | Valor |
|-----------|-------|
| Height | 36–40px |
| Padding | 9px 12px |
| Border radius | 7px |
| Font size | 13px |
| Border default | 0.5px `--border` |
| Border focus | 1px `--brand-action` + ring `0 0 0 3px rgba(action, 0.1)` |
| Border error | 1px `--danger` + ring `0 0 0 3px rgba(danger, 0.1)` |
| Placeholder | `--text-hint` |
| Label position | Encima del campo (nunca flotante) |
| Label style | 11px · 600 · uppercase · `--text-secondary` · 0.04em |
| Helper text | 11px · `--text-muted` · margin-top 4px |
| Error text | 11px · `--danger` · margin-top 4px |

### Reglas

| ✓ | ✗ |
|---|---|
| Labels siempre visibles | Placeholder como único label |
| Validar al perder foco (blur) | Validar solo al submit |
| Mensaje de error por campo específico | Lista de errores al inicio |
| Indicar campos obligatorios | Asumir que el usuario adivina |

---

## 8. Badges de Estado

### Spec base

```css
.badge {
  font-size: 10px;
  font-weight: 500;
  padding: 3px 10px;
  border-radius: 20px; /* pill */
  display: inline-flex;
  align-items: center;
  gap: 4px; /* si tiene ícono */
}
```

### Variantes

| Badge | Background | Color | Ejemplo |
|-------|-----------|-------|---------|
| Success | `--success-bg` | `--success` | Entregado, Confirmado, Activo |
| Warning | `--warning-bg` | `--warning` | En camino, Pendiente, En proceso |
| Danger | `--danger-bg` | `--danger` | Cancelado, Rechazado, Vencido |
| Info | `--info-bg` | `--info` | En revisión, Abierto, Nuevo |
| Neutral | `--surface-soft` | `--text-secondary` | Borrador, Inactivo, Pausado |

### Reglas de badges

- Los colores semánticos de badges son **absolutos** — no cambian por tenant.
- Siempre incluir texto descriptivo (no solo color, por accesibilidad).
- Opcionalmente incluir ícono (dot o symbol) antes del texto.
- No usar `--tenant-accent` para badges.

---

## 9. Cards de Métricas

### Estructura

```
┌─────────────────────┐
│ LABEL               │  ← 10px · uppercase · --text-muted · 0.06em
│ $1,240              │  ← 20–24px · 700 · --tenant-accent
│ ↑ 12% vs ayer       │  ← 11px · --success / --danger / --text-muted
└─────────────────────┘
```

### Specs

```css
.metric-card {
  background: var(--surface);
  border: 0.5px solid var(--border-light);
  border-radius: 8px;
  padding: 12px 16px;
}
.metric-label {
  font-size: 10px;
  font-weight: 600;
  color: var(--text-muted);
  letter-spacing: 0.06em;
  text-transform: uppercase;
  margin-bottom: 4px;
}
.metric-value {
  font-size: 22px;
  font-weight: 700;
  color: var(--tenant-accent);
  line-height: 1.2;
}
.metric-delta {
  font-size: 11px;
  margin-top: 4px;
}
.metric-delta--positive { color: var(--success); }
.metric-delta--negative { color: var(--danger); }
.metric-delta--neutral  { color: var(--text-muted); }
```

### Grid

| Breakpoint | Columnas | Gap |
|-----------|----------|-----|
| Desktop (>1024px) | 3–4 | 10–12px |
| Tablet (768–1024) | 2 | 10px |
| Mobile (<768) | 1 (stack) | 8px |

---

## 10. Layout del Dashboard

### Estructura

```
┌────────────┬──────────────────────────────────────────┐
│  SIDEBAR   │  TOPBAR (sticky)                         │
│  200px     │  44px                                    │
│  --brand-  ├──────────────────────────────────────────┤
│  dark      │                                          │
│            │  CONTENIDO                               │
│  ┌──────┐  │  bg: --surface-soft                      │
│  │Avatar│  │  padding: 16–24px                        │
│  │Name  │  │                                          │
│  │Plan  │  │  ┌──── ──── ──── ────┐                  │
│  └──────┘  │  │ Grid de métricas  │                  │
│            │  └───────────────────┘                  │
│  Nav       │                                          │
│  Nav       │  ┌─────────────────────────────────┐    │
│  Nav       │  │ Card de contenido principal     │    │
│  Nav       │  │ (tabla, lista, detalle)         │    │
│            │  └─────────────────────────────────┘    │
│            │                                          │
│  ────────  │                                          │
│  powered   │                                          │
│  by PROD   │                                          │
└────────────┴──────────────────────────────────────────┘
```

### Dimensiones

| Elemento | Valor |
|----------|-------|
| Sidebar width | 180–220px |
| Sidebar bg | `--brand-dark` |
| Topbar height | 44–52px |
| Topbar bg | `--surface` |
| Content bg | `--surface-soft` |
| Content padding | 16–24px |
| Max content width | Sin máximo (full width menos sidebar) |
| Grid métricas gap | 10–12px |

### Responsive

| Breakpoint | Sidebar | Métricas | Tablas |
|-----------|---------|----------|--------|
| >1024px | Visible fijo | 3–4 cols | Tabla normal |
| 768–1024px | Drawer (colapsable) | 2 cols | Tabla con scroll-x |
| <768px | Drawer (hamburguesa) | 1 col stack | Cards en lugar de tabla |

En mobile:
- Hamburguesa en el topbar (izquierda)
- Logo/avatar del tenant en el topbar (centro o derecha)
- Sidebar se convierte en drawer slide-from-left con overlay

---

## 11. URLs y Subdominios

### Patrón

```
https://{slug-del-tenant}.{producto}.co
```

### Ejemplos

| URL | Qué es |
|-----|--------|
| `https://ordamy.co` | Landing pública del producto |
| `https://burgerscraft.ordamy.co` | Dashboard del tenant "Burger Craft" |
| `https://pizzazeta.ordamy.co` | Dashboard del tenant "Pizza Zeta" |

### Reglas

| Regla | Detalle |
|-------|---------|
| Holding en URL | **Nunca aparece** en URLs públicas de productos |
| Generación del slug | Automático desde nombre del negocio en onboarding |
| Editable | Sí, en configuración del tenant |
| Caracteres permitidos | `a-z`, `0-9`, `-` (no guiones al inicio/fin) |
| Longitud | 3–48 caracteres |
| Reservados | `www`, `app`, `admin`, `api`, `static`, `cdn` |

### Metadatos web

| Meta | Valor |
|------|-------|
| Favicon | Isotipo del producto (no del tenant) |
| `<title>` | `{Nombre Tenant} · {Producto}` ej: "Burger Craft · ORDAMY" |
| `theme-color` | `--brand-dark` |
| OG Image | Branded del producto (landing) o genérico del tenant (dashboard) |

---

## 12. Tono de Voz

### Por nivel

| Nivel | Carácter | Ejemplos |
|-------|----------|----------|
| **Holding** | Institucional, legal. Solo formales. | "Bigso S.A.S., desarrollador de ORDAMY" · "© 2026 Bigso S.A.S." |
| **Producto** | Directo, empoderador, sin jerga. | "Optimiza tu negocio" · "Gestión en una sola plataforma" · "Plataforma gestionada por ORDAMY" |
| **Sistema → Tenant** | 2ª persona directa. Breve. Práctico. | "Buenos días, Burger Craft" · "5 órdenes pendientes" · "Tu panel está listo" |

### Reglas de nomenclatura

| ✓ Correcto | ✗ Incorrecto |
|-----------|-------------|
| Burger Craft (nombre propio) | burger craft (todo minúsculas) |
| Burger Craft | BURGER CRAFT (todo mayúsculas) |
| "powered by ORDAMY" | "powered by Bigso" |
| "Plataforma gestionada por ORDAMY" | "Software de Bigso S.A.S." |

### Tono por pantalla

| Pantalla | Tono | Ejemplo |
|----------|------|---------|
| Landing hero | Aspiracional, conciso | "El control que tu negocio necesita" |
| Onboarding | Guiado, cercano | "Vamos a configurar tu negocio. Paso 1 de 4." |
| Dashboard | Informativo, sin decoración | "3 órdenes nuevas" |
| Error | Humano, con acción | "No pudimos guardar. Intenta de nuevo." |
| Vacío | Motivacional + accionable | "Sin órdenes aún. Tu primera venta está por llegar." |

---

## 13. Estados del Sistema

### 13.1 Loading

| Tipo | Cuándo | Spec |
|------|--------|------|
| **Skeleton** | Carga inicial de dashboard/página | Shapes con animate-pulse · color `--border-light` |
| **Spinner** | Submit de formulario, acciones | SVG 16–20px con animate-spin dentro del botón |
| **Progress** | Upload, procesos con duración | Barra horizontal con `--brand-action` · porcentaje |
| **Optimistic** | Toggle, like, acciones rápidas | UI cambia inmediato, revierte si falla |

### 13.2 Empty States

Estructura obligatoria:

```
┌─────────────────────────────────┐
│                                 │
│      [ Ilustración/Ícono ]      │  ← 40–64px · --text-hint
│                                 │
│      Título descriptivo         │  ← 14px · 600 · --text-primary
│      Explicación breve          │  ← 13px · --text-muted
│                                 │
│      [ CTA: Crear primero ]     │  ← Botón primary o outline
│                                 │
└─────────────────────────────────┘
```

Todo empty state **debe tener una acción**. Nunca dejar al usuario sin siguiente paso.

### 13.3 Error States

| Tipo | Posición | Formato |
|------|----------|---------|
| Validación | Inline debajo del campo | Texto `--danger` + borde rojo |
| Acción fallida | Toast top-right | Card con ícono + texto + dismiss (auto 5s) |
| Conexión | Banner sticky top | Full-width · `--warning-bg` · "Reconectando..." |
| 500/Fatal | Centro de página | Ilustración + "Algo salió mal" + retry |

### 13.4 Toasts / Notifications

```
┌──────────────────────────────────┐
│ ✓ Orden #1042 marcada como       │
│   entregada                      │
│                              [×] │
└──────────────────────────────────┘
```

| Spec | Valor |
|------|-------|
| Posición | Top-right, z-50 |
| Width | 320–400px |
| Radius | 8px |
| Shadow | `--shadow-elevated` |
| Auto-dismiss | 5 segundos (errores: manual dismiss) |
| Stack | Máximo 3 visibles, los demás quedan en cola |

---

## 14. Iconografía

### Set recomendado

Heroicons (outline, 1.5px stroke) como base. Cada producto puede usar Lucide o Phosphor si mantiene consistencia interna.

### Reglas

| Regla | Detalle |
|-------|---------|
| **Solo SVG** | Emojis en UI están **prohibidos** |
| **Outline por defecto** | Variante solid solo para nav active |
| **currentColor** | Siempre heredar del contexto |
| **Un solo set** | No mezclar librerías en el mismo producto |

### Tamaños

| Contexto | Size |
|----------|------|
| Nav sidebar | 18–20px |
| Dentro de botones | 16px |
| Badges/inline | 14px |
| Feature cards (landing) | 24px |
| Empty states | 40–48px |
| Hero decorativos | 64px |

### Color

| Contexto | Color |
|----------|-------|
| Nav (fondo oscuro) inactive | rgba(255,255,255, 0.55) |
| Nav active | white |
| Botón primary | white |
| Botón ghost/outline | `--brand-action` o `--text-secondary` |
| Estado semántico | Token del estado |
| Decorativo (empty state) | `--text-hint` |

---

## 15. Animaciones

### Principios

1. **Funcionales**: Indican qué pasó y dónde está el cambio.
2. **Breves**: 150–300ms. Nunca más de 500ms para interacciones.
3. **Naturales**: `ease-out` para entradas, `ease-in` para salidas.
4. **Prescindibles**: El contenido se entiende sin animación.

### Transiciones comunes

| Efecto | Duración | Easing | Uso |
|--------|----------|--------|-----|
| Color/opacity | 150ms | ease-out | Hover, focus, badges appear |
| Transform (scale) | 150ms | ease-out | Button press, popover |
| Slide | 200–300ms | ease-out | Drawer, sidebar mobile |
| Fade + slide | 200ms | ease-out | Modales, toasts |

### CSS base

```css
/* Interacciones de UI */
transition: all 150ms ease-out;

/* Modales y overlays */
transition: opacity 200ms ease-out, transform 200ms ease-out;

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
  * { transition-duration: 0.01ms !important; animation-duration: 0.01ms !important; }
}
```

---

## 16. Data Visualization

### Paleta para gráficos

Cuando un dashboard necesita gráficos (charts), usar estos colores en orden:

| # | Uso | Token/Valor |
|---|-----|-------------|
| 1 | Serie primaria | `--tenant-accent` |
| 2 | Serie secundaria | `--brand-action` al 60% opacity |
| 3 | Serie terciaria | `--text-secondary` |
| 4+ | Series adicionales | Variantes del `--tenant-accent` (±30° hue) |

### Reglas

- No más de 5 colores en un solo gráfico (usar "otros" para el resto).
- Labels siempre legibles (mínimo 11px).
- Tooltips con font-size 12px, padding 8px 12px, radius 6px.
- Eje Y siempre inicia en 0 para barras (evitar manipulación visual).
- Incluir texto alternativo descriptivo para accesibilidad.

---

## 17. Email Templates

### Estructura del email transaccional

```
┌──────────────────────────────────────────┐
│  [ Logo Tenant ]  Nombre del Tenant      │  ← Header
├──────────────────────────────────────────┤
│                                          │
│  Título del email                        │
│  Contenido principal                     │
│                                          │
│  [ CTA Button ]                          │
│                                          │
├──────────────────────────────────────────┤
│  Enviado por PRODUCTO                    │  ← Footer
│  bigso.co                                │
│  Desuscribirse                           │
└──────────────────────────────────────────┘
```

### Specs

| Elemento | Spec |
|----------|------|
| Max width | 600px |
| Font | System font stack (no cargar Inter en email) |
| Header | Logo tenant (max 40px height) + nombre 16px/700 |
| Body font | 15px / line-height 1.6 |
| CTA button | Padding 12px 24px · radius 6px · `--tenant-accent` bg · white text |
| Footer | 12px · gris · "Enviado por PRODUCTO" · link desuscribir |
| Holding en email | **No aparece** en el cuerpo. Solo en footer si legal lo requiere. |

---

## 18. Accesibilidad

### Contraste (WCAG 2.1 AA)

| Tipo | Ratio mínimo |
|------|-------------|
| Texto normal (<18px) | ≥ 4.5:1 |
| Texto grande (≥18px o ≥14px bold) | ≥ 3:1 |
| Componentes UI y gráficos | ≥ 3:1 |

### Focus visible

```css
:focus-visible {
  outline: 2px solid var(--brand-action);
  outline-offset: 2px;
}
/* En sidebar oscuro: */
.sidebar :focus-visible {
  outline-color: var(--tenant-accent);
}
```

### Requisitos

| Requisito | Detalle |
|-----------|---------|
| Labels | Todos los inputs con `<label for>` o `aria-label` |
| Focus | Visible en todos los interactivos, nunca `outline: none` sin reemplazo |
| Color alone | No depender solo del color para estado (agregar ícono/texto) |
| Keyboard | Tab, Enter, Space, Escape funcionales en toda la UI |
| Alt text | En imágenes significativas. Avatares con iniciales: `aria-label` |
| Screen reader | `aria-live="polite"` para toasts y notificaciones |
| Reduced motion | `prefers-reduced-motion` respetado |

### Validación de color del tenant

Antes de aceptar un color personalizado:
1. Texto blanco sobre color: ratio ≥ 4.5:1
2. Color sobre fondo blanco: ratio ≥ 3:1
3. No confundible con `--danger` o `--success`

Fallback: si no pasa → usar `--brand-action`.

---

## 19. Reglas Absolutas

### Prohibiciones (sin excepciones)

| # | Regla |
|---|-------|
| 1 | **No holding en el dashboard.** Bigso no aparece en el panel del tenant. Solo landing y legal. |
| 2 | **No ocultar el producto.** Siempre visible como watermark mínimo ("powered by PRODUCTO"). |
| 3 | **No igualar tamaños.** Logo del tenant SIEMPRE más grande que referencia al producto en su contexto. |
| 4 | **No 3 marcas a la par.** Máximo 2 marcas visibles, con jerarquía clara. |
| 5 | **No acento para errores.** `--brand-action` / `--tenant-accent` es SOLO para acciones positivas. |
| 6 | **No "powered by BIGSO".** Siempre "powered by PRODUCTO". El holding no se expone al usuario final. |
| 7 | **No emojis como iconos.** Solo SVG. |
| 8 | **No color-only states.** Badges y estados siempre con texto/ícono + color. |
| 9 | **No placeholder-only inputs.** Labels visibles obligatorios. |
| 10 | **No múltiples CTAs primarios.** Uno por pantalla/sección visible. |

### Obligaciones

| # | Regla |
|---|-------|
| 1 | Nombre del tenant siempre como nombre propio (mayúscula inicial). |
| 2 | `--tenant-accent` reemplaza `--brand-action` dentro del panel del tenant. |
| 3 | Contraste WCAG AA en todo texto legible. |
| 4 | Focus visible en todos los interactivos. |
| 5 | Empty states con acción (nunca dejar al usuario sin siguiente paso). |
| 6 | Loading skeleton para toda carga > 300ms. |
| 7 | `prefers-reduced-motion` respetado. |
| 8 | Emails usan la identidad del tenant como remitente, producto solo en footer. |

---

## 20. Checklists por Pantalla

### Landing pública

- [ ] Logo del producto prominente en navbar (15–17px · 800)
- [ ] "by BIGSO" discreto junto al logo (10px · gris)
- [ ] Sin referencia al tenant ni a subdominios
- [ ] Footer con copyright del holding
- [ ] CTA en `--brand-action`
- [ ] Fondo cálido en hero (`--brand-bg`, no blanco puro)
- [ ] Tipografía hero: 28–32px · 800
- [ ] Contraste WCAG AA en todo texto
- [ ] Sin emojis como iconos (solo SVG)
- [ ] Responsive: 375px, 768px, 1024px, 1440px

### Login contextual del tenant

- [ ] Avatar/logo del tenant centrado (52×52px · radius 12px)
- [ ] Nombre del tenant como elemento principal
- [ ] URL subdominio visible bajo nombre
- [ ] "Plataforma gestionada por PRODUCTO" en footer del card
- [ ] "un producto de BIGSO" segunda línea, casi invisible
- [ ] Botón con `--tenant-accent` (o `--brand-action` si no white-label)
- [ ] Holding no aparece en ningún otro lugar del card
- [ ] Focus visible en inputs y botón
- [ ] Labels en todos los campos

### Onboarding / registro

- [ ] Logo del producto prominente en navbar
- [ ] Indicador de paso: "Paso X de Y"
- [ ] Sin mencionar holding hasta pie (TyC)
- [ ] Tono guiado y cercano
- [ ] Sin referencia al tenant (en construcción)
- [ ] CTA en `--brand-action`
- [ ] Labels + helper text en todos los campos
- [ ] Validación inline al perder foco

### Dashboard interno

- [ ] Avatar/logo tenant en header del sidebar
- [ ] `--tenant-accent` en métricas, CTAs y nav active
- [ ] "powered by PRODUCTO" solo en pie del sidebar (9px · 20% opacity)
- [ ] Holding completamente **ausente**
- [ ] Saludo con nombre del tenant en topbar
- [ ] Logo del producto **no** en área de contenido ni topbar
- [ ] Badges solo con colores semánticos (no tenant-accent)
- [ ] Empty states con acción
- [ ] Skeleton loading para datos > 300ms
- [ ] Toasts para feedback de acciones
- [ ] Responsive sidebar → drawer en mobile
- [ ] Nav icons son SVG (no emojis)

### Emails transaccionales

- [ ] Header: logo/avatar del tenant + nombre
- [ ] CTA con `--tenant-accent`
- [ ] Footer: "Enviado por PRODUCTO" (no holding)
- [ ] Link de desuscripción visible
- [ ] Max-width 600px
- [ ] System fonts (no depender de webfonts)

---

## Apéndice: Design Tokens Completos

```css
:root {
  /* ═══ MARCA (definir por producto) ═══ */
  --brand-dark: ;           /* Sidebar, navbars, tipografía de peso */
  --brand-action: ;         /* CTAs, highlights (NUNCA para errores) */
  --brand-bg: ;             /* Fondo cálido público */

  /* ═══ TENANT ═══ */
  --tenant-accent: var(--brand-action); /* Override en white-label */

  /* ═══ NEUTROS ═══ */
  --text-primary: ;         /* WCAG AA+ contra surface */
  --text-secondary: ;       /* WCAG AA contra surface */
  --text-muted: ;           /* WCAG AA mínimo */
  --text-hint: ;            /* Solo decorativo */
  --surface: ;              /* Blanco o casi blanco */
  --surface-soft: ;         /* Gris suave (background de contenido) */
  --border: ;               /* Bordes principales */
  --border-light: ;         /* Divisores casi invisibles */

  /* ═══ SEMÁNTICOS (absolutos, no cambian por tenant) ═══ */
  --success: ;
  --success-bg: ;
  --warning: ;
  --warning-bg: ;
  --danger: ;
  --danger-bg: ;
  --info: ;
  --info-bg: ;

  /* ═══ LAYOUT ═══ */
  --sidebar-width: 200px;
  --topbar-height: 44px;
  --content-padding: 24px;

  /* ═══ RADII ═══ */
  --radius-btn: 8px;
  --radius-input: 7px;
  --radius-sm: 8px;
  --radius-md: 10px;
  --radius-lg: 14px;
  --radius-pill: 20px;

  /* ═══ TIPOGRAFÍA ═══ */
  --font-sans: 'Inter', system-ui, -apple-system, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* ═══ SOMBRAS ═══ */
  --shadow-card: 0 1px 3px rgba(0,0,0,0.07), 0 4px 12px rgba(0,0,0,0.04);
  --shadow-elevated: 0 4px 16px rgba(0,0,0,0.10), 0 1px 4px rgba(0,0,0,0.06);

  /* ═══ TRANSICIONES ═══ */
  --transition-fast: 150ms ease-out;
  --transition-normal: 200ms ease-out;
  --transition-slow: 300ms ease-out;
}
```

---

*Apps by Bigso · Design System v4.0 · Mayo 2026*
*Mantenido por el equipo de producto de Bigso*
