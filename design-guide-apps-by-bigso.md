# apps by bigso · Sistema de Diseño

## Guía Oficial de Diseño y Co-branding

**Versión 1.0 · Mayo 2026**

---

## Introducción

Esta guía establece el sistema de diseño para todas las aplicaciones desarrolladas bajo el paraguas de **bigso**. Su propósito es garantizar coherencia visual, experiencia de usuario consistente y una identidad de marca reconocible a través de todos los productos digitales que forman parte del ecosistema bigso.

El sistema está diseñado con tres niveles de marca que operan en diferentes contextos: el nivel corporativo (bigso), el nivel de producto (la aplicación específica) y el nivel de cliente (el tenant o negocio que utiliza la plataforma). Cada nivel tiene su rol definido y su presencia apropiada según el contexto de uso.

La filosofía central del sistema se basa en la **claridad jerárquica**: cada usuario debe saber exactamente dónde se encuentra dentro del ecosistema y quién respalda la experiencia que está utilizando. bigso proporciona la confianza institucional, la aplicación específica ofrece la funcionalidad que el usuario busca, y el tenant personaliza la experiencia para su propio contexto de negocio.

---

## 1. Arquitectura de Marca

### 1.1 Jerarquía de Marcas

El ecosistema bigso está estructurado en tres niveles claramente diferenciados, cada uno con responsabilidades y presencia visual específicas:

```
bigso  (corporativo / holding)
  └── [Aplicación]  (producto SaaS: ORDAMY, u otra)
        └── Tenant  (negocio cliente: restaurantes, tiendas, servicios)
```

Esta jerarquía no es simplemente organizativa; define cómo cada marca aparece en la interfaz y cómo se relacionan entre sí. El principio fundamental es que **a mayor profundidad en el producto, menor presencia de los niveles superiores**. El tenant debe sentirse dueño de su experiencia, mientras que bigso y el producto permanecen como respaldos silenciosos pero reconocibles.

### 1.2 Roles de Cada Marca

**bigso** representa la entidad corporativa que desarrolla y respalda las aplicaciones. Su aparición debe ser institucional, técnica cuando sea necesario y siempre discreta en contextos de usuario final. Aparece principalmente en elementos legales, documentación técnica y pantallas de marketing de alto nivel donde la credibilidad corporativa añade valor.

**La Aplicación** (ORDAMY u otra del ecosistema) es el producto que el mercado adquiere y utiliza directamente. Es la voz principal de marketing, el protagonista en las pantallas públicas y el elemento de marca que el usuario final asocia con la funcionalidad que recibe. Debe ser reconocible, memorable y transmitir profesionalismo.

**El Tenant** es el negocio del cliente que utiliza la plataforma. Es lo que el usuario final del cliente reconoce como "su marca" cuando interactúa con el sistema. El tenant debe tener control visual sobre su espacio de trabajo, con su identidad predominando en el dashboard y las interfaces de operación.

### 1.3 Principio de Invisibilidad Progresiva

La regla de oro del sistema establece que cuanto más profundo está el usuario dentro del producto, más desaparece la marca corporativa y la marca del producto. Esto no significa eliminación completa, sino reducción progresiva de la presencia visual hasta alcanzar un nivel mínimo de reconocimiento.

Este principio tiene bases en experiencia de usuario: el usuario que ha iniciado sesión en su panel de negocio no necesita recordatorios constantes de quién desarrolló el software. Lo que necesita es acceso rápido a sus herramientas y una interfaz que refleje su negocio. La marca corporativa se convierte en un símbolo de confianza implícita, presente pero no intrusiva.

---

## 2. Presencia por Pantalla

### 2.1 Tabla de Visibilidad

Cada pantalla del sistema tiene una distribución de presencia de marca asignada que define qué elementos deben ser prominentes y cuáles deben permanecer discretos:

| Pantalla | Aplicación | Tenant | bigso |
|---|---|---|---|
| Landing pública | Protagonista | Ausente | Solo nav + footer |
| Login contextual | Secundario | Protagonista | Invisible |
| Onboarding | Principal | En construcción | Solo términos legales |
| Dashboard interno | Watermark mínimo | Protagonista | Invisible |

### 2.2 Reglas de Visibilidad por Marca

**bigso aparece únicamente en:**

- Barra de navegación de landing: como referencia secundaria junto al logo de la aplicación, en formato discretamente identificable
- Pie de página de landing: en textos legales y derechos reservados
- Pie de formularios de registro: en menciones legales que el usuario acepta al crear cuenta
- Documentación y materiales legales externos
- **Nunca** dentro del panel operativo del tenant

**La Aplicación aparece en:**

- Landing: como logo principal en navegación, área hero y todas las pantallas de marketing
- Onboarding: como elemento gráfico prominente en cada paso del proceso
- Login del tenant: como referencia secundaria con texto de gestión
- Dashboard: como watermark extremadamente discreto en el sidebar
- Correos electrónicos transaccionales: como elemento de pie de página

**El Tenant aparece en:**

- Login contextual: logo, nombre comercial, color de acento característico
- Dashboard: sidebar, mensaje de bienvenida, color de acento en llamadas a acción y métricas
- Subdominio de la URL: visible en el navegador como identificador del negocio
- Notificaciones y comunicaciones: como remitente identificado

### 2.3 Distribución de Atención Visual

En cualquier pantalla donde convivan múltiples marcas, la distribución de atención visual debe seguir una proporción clara. El elemento más importante (protagonista) debe capturar aproximadamente el 70% de la atención inicial, el elemento secundario el 25%, y cualquier referencia terciaria el 5% restante.

Esta distribución se logra mediante tamaño, color de acento, posición en la jerarquía visual y peso tipográfico. Cuando el tenant es protagonista, su avatar y nombre deben ser los primeros elementos que el usuario identifica. Cuando la aplicación es protagonista en landing, su logo y elementos de marca deben dominar el campo visual superior.

---

## 3. Sistema de Paleta de Colores

### 3.1 Filosofía del Sistema de Color

El sistema de color está diseñado para ser **adaptable** mientras mantiene coherencia estructural. En lugar de especificar colores exactos con valores hexadecimales, el sistema define roles, temperaturas y relaciones que pueden implementarse con diferentes paletas según el contexto específico de cada aplicación dentro del ecosistema bigso.

Esta aproximación permite que ORDAMY tenga su identidad visual característica mientras otras aplicaciones del ecosistema pueden desarrollar sus propios esquemas de color, todos siguiendo los mismos principios estructurales. La guía proporciona las reglas; la paleta específica se define en el nivel de aplicación individual.

### 3.2 Roles del Color

Cada color en el sistema cumple un rol específico que define su función y dónde puede utilizarse:

**Colores Primarios de Marca**

Son los colores que identifican inmediatamente a la aplicación o marca. Normalmente incluyen un color oscuro o profundo para tipografía y elementos estructurales, y un color de acento vibrante para llamadas a acción y destacados. Los colores primarios de marca nunca se utilizan para estados de error o advertencias.

**Colores de Fondo**

Definen el ambiente visual de las interfaces. Incluyen un fondo principal claro (para páginas públicas y áreas de contenido) y fondos de superficie (para cards y elementos elevados). Los fondos deben tener suficiente contraste con el texto sin ser tan oscuros que dominen la composición.

**Colores de Texto**

Establecen jerarquía lectora mediante variaciones de peso visual. Incluyen color de texto primario (para contenido importante), texto secundario (para soporte y labels), texto terciario (para hints y ayudas) y texto legal (para menciones mínimas como watermarks).

**Colores de Estado**

Indican el estado de procesos, órdenes o elementos de interfaz. Cada estado tiene un color de texto y un color de fondo asociado que deben mantener relación tonal (el fondo es una versión pastel del color de texto). Los estados estándar son: éxito (verde asociado a completación), advertencia (amarillo/ámbar asociado a atención needed), error (rojo asociado a problemas) e información (azul asociado a neutral informational).

### 3.3 Estructura de la Paleta

La paleta se organiza en categorías que definen qué colores usar según el contexto:

```
Paleta de Marca (definida por aplicación)
├── Color primario oscuro
├── Color de acento
└── Color de fondo cálido

Paleta Neutra (compartida)
├── Textos primarios
├── Textos secundarios
├── Textos terciarios
└── Superficies y bordes

Paleta de Estados (compartida)
├── Éxito (texto + fondo)
├── Advertencia (texto + fondo)
├── Error (texto + fondo)
└── Información (texto + fondo)
```

### 3.4 Temperatura y Carácter

Los colores de cada aplicación deben mantener una temperatura consistente. Una paleta cálida (tonos foundationados en rojos, naranjas, amarillos) transmite cercanía, accesibilidad y dinamismo. Una paleta fría (tonos foundationados en azules, verdes, grises) transmite profesionalismo, estabilidad y tecnología.

Para aplicaciones orientadas a negocios de consumo como restaurantes o retail, se recomienda una paleta con temperatura cálida que invite a la interacción y transmita vitalidad. Para aplicaciones orientadas a procesos empresariales o administración, una paleta más neutra puede ser más apropiada.

La temperatura no se refiere únicamente al color de acento, sino a toda la paleta: los grises deben inclinationarse hacia tonos cálidos o fríos según el carácter general deseado.

### 3.5 Contraste y Accesibilidad

Todos los colores de texto deben cumplir con estándares mínimos de contraste WCAG 2.1 nivel AA:

- Texto normal sobre fondo: ratio mínimo de 4.5:1
- Texto grande (18px+ o 14px+ bold) sobre fondo: ratio mínimo de 3:1
- Elementos gráficos y componentes de interfaz: ratio mínimo de 3:1 contra colores adyacentes

Los colores de estado deben ser claramente distinguibles entre sí. Un usuario con daltonismo debe poder identificar el estado de un elemento sin depender únicamente del color. Siempre que sea posible, complementar con iconografía o texto.

### 3.6 Color del Tenant

En implementaciones estándar, el color de acento del tenant se reemplaza por el color de acento de la aplicación. Cuando el sistema soporta white-label, cada tenant puede especificar su propio color de acento que reemplaza al color de acento de la aplicación únicamente en el contexto de su panel.

El color del tenant debe mantener visibilidad adecuada contra fondos claros y oscuros utilizados en el dashboard. Probar siempre la legibilidad del texto en blanco o negro sobre el color del tenant antes de implementar.

---

## 4. Tipografía

### 4.1 Filosofía Tipográfica

El sistema tipográfico prioriza la legibilidad en pantallas de diversos tamaños y condiciones de visualización. Se seleccionan fuentes que funcionan bien tanto en retina como en pantallas estándar, con formas de letras que mantienen claridad a tamaños pequeños.

La tipografía establece jerarquía visual a través de tamaño, peso y color. No se utilizan decoraciones tipográficas (sombras, contornos, efectos 3D) para crear jerarquía. La simplicidad tipográfica transmite profesionalismo y asegura que los elementos importantes se identifiquen por su contenido, no por tratamiento visual.

### 4.2 Escala Tipográfica

La escala define los tamaños estándar para cada uso, creando una progresión predecible que facilita el diseño y desarrollo:

| Uso | Tamaño Relativo | Peso | Aplicación |
|---|---|---|---|
| Títulos hero | Extremo grande | Extra bold | Impacto en landing |
| Títulos de sección | Grande | Bold | Headers de contenido |
| Títulos de card | Mediano grande | Semi bold | Elementos destacados |
| Cuerpo de texto | Base | Regular | Contenido principal |
| Labels y captions | Pequeño | Medium | Texto de soporte |
| Texto legal | Mínimo | Regular | Menciones y metadata |

La escala debe mantener relaciones proporcionales armónicas. Un incremento del 20-30% entre niveles adyacentes crea una progresión natural sin saltos abruptos.

### 4.3 Jerarquía de Color en Tipografía

El color tipográfico comunica importancia y rol:

- **Títulos principales**: Color oscuro profundo, máximo contraste contra el fondo
- **Highlights y énfasis de marca**: Color de acento de la marca, utilizado con moderación para destacar elementos específicos
- **Cuerpo de texto**: Color de texto primario, contraste suficiente para lectura extendida
- **Texto de soporte**: Color de texto secundario, diferenciación clara pero menos prominencia
- **Texto de ayuda y hints**: Color de texto terciario, apenas visible pero presente cuando se busca
- **Texto legal y watermarks**: Color de texto mínimo, diseñado para ser ignorado visualmente

### 4.4 Espaciado Tipográfico

El espaciado entre líneas (line-height) debe ser proporcional al tamaño del texto:

- Títulos: line-height entre 1.2 y 1.3 para densidad
- Cuerpo de texto: line-height entre 1.5 y 1.6 para legibilidad
- Labels y texto pequeño: line-height entre 1.4 y 1.5

El espaciado entre letras (letter-spacing) se utiliza con moderación:

- Títulos en mayúsculas: tracking amplio (+0.05em a +0.1em)
- Texto legal: tracking ligeramente amplio
- Texto normal: tracking por defecto o ligeramente reducido

### 4.5 Tipografía por Contexto

**Contexto público (landing, marketing)**: Tipografía con personalidad más marcada, posible combinación de familias para crear distinción entre títulos y cuerpo.

**Contexto operativo (dashboard, panel)**: Tipografía funcional con mejor legibilidad a múltiples tamaños, posible uso de familias más neutrales que no distraigan de los datos.

**Contexto mobile**: Tipografía ligeramente más grande para el mismo elemento, mayor line-height para facilitar lectura en pantallas pequeñas.

---

## 5. Componentes de Co-branding

### 5.1 Navbar de Landing Pública

La barra de navegación de landing establece el primer contacto visual del usuario con la aplicación. Su composición debe seguir esta estructura:

```
[ Logo Aplicación ]  [ "by bigso" ]                    [ Acción 1 ]  [ Acción 2 ]
```

El logo de la aplicación ocupa la posición izquierda con prominencia visual. bigso se presenta como referencia corporativa inmediatamente después, con diferenciación visual clara que establece la relación jerárquica sin competir por atención. Las acciones de navegación ocupan el extremo derecho en orden de prioridad.

**Especificaciones de estilo:**

- Altura de navbar: compacta pero funcional (44-56px)
- Fondo: color superficie con borde inferior sutil
- Separador entre logo de aplicación y "by bigso": línea vertical o elemento gráfico discreto
- Logo de aplicación: peso extra bold, tamaño que equilibre presencia con economía de espacio
- Referencia bigso: tamaño significativamente menor, color terciario
- Acciones: buttons en estilo primario y secundario según jerarquía

### 5.2 Footer de Landing Pública

El pie de página de landing cumple funciones legales y de navegación secundaria:

- Texto de copyright centrado
- Fondo en color superficie suave (ligeramente diferenciado del fondo principal)
- Altura compacta
- Posibles enlaces a términos, privacidad, contacto
- Referencia a bigso integrada en texto de copyright

### 5.3 Login Contextual del Tenant

La pantalla de login del tenant es crítica porque debe comunicar inmediatamente cuál es el negocio del cliente mientras mantiene la referencia a la aplicación que lo gestiona.

**Estructura del card de login:**

```
┌─────────────────────────────────┐
│                                 │
│      [ Logo Tenant 52×52 ]      │
│      Nombre del Tenant          │
│      subdomain.app.co           │
│                                 │
│      [ Campos de acceso ]       │
│      [ Botón de entrada ]       │
│                                 │
│  Plataforma gestionada por      │
│  [ Aplicación ]                 │
│  un producto de bigso           │
│                                 │
└─────────────────────────────────┘
```

El logo del tenant debe ser el elemento más prominente del card. El nombre comercial sigue en jerarquía visual. El subdominio proporciona contexto técnico sin ser intrusivo. La referencia a la aplicación aparece en el footer del card con peso visual menor.

### 5.4 Sidebar del Dashboard

El sidebar del dashboard es el elemento de navegación principal dentro del panel del tenant. Su diseño debe priorizar la usabilidad mientras establece la identidad del tenant.

**Estructura del sidebar:**

```
┌──────────────────┐
│ [Logo] Nombre    │
│        Plan      │
├──────────────────┤
│                  │
│  Navegación      │
│  Navegación      │
│  Navegación      │
│                  │
├──────────────────┤
│ powered by       │
│ [Aplicación]     │
└──────────────────┘
```

El header del sidebar presenta el tenant con su logo e información de plan. Los items de navegación tienen iconografía clara y etiquetas legibles. El footer del sidebar contiene únicamente la referencia "powered by [Aplicación]" en texto muy discreto, casi invisible pero presente para quien busque establecer la procedencia del software.

**bigso NO aparece en el sidebar del dashboard.**

### 5.5 Sellos "Powered By" — Variantes

El sello de marca que indica la procedencia del software se implementa de diferentes formas según el contexto:

| Contexto | Formato | Estilo Visual |
|---|---|---|
| Sidebar oscuro | "powered by [Aplicación]" | 9px, color blanco al 20% de opacidad, solo texto |
| Card de login | "Plataforma gestionada por [Aplicación]" | Texto pequeño, nombre de aplicación en negrita |
| Correos transaccionales | Logo pequeño + "by bigso" | En footer del email, integrado discretamente |
| Documentos PDF | "Generado por [Aplicación] · bigso.co" | Texto mínimo en pie de página, casi invisible |

### 5.6 Implementación de Logo de Aplicación

El logo de la aplicación debe estar disponible en múltiples formatos para diferentes contextos:

- **Formato horizontal completo**: Para navbar de landing y materiales de marketing
- **Formato de ícono**: Para espacios reducidos como avatars y favicon
- **Versión monocromática**: Para aplicación sobre fondos oscuros o de color
- **Versión invertida**: Para aplicación sobre fondos muy oscuros

El archivo de logo debe proporcionarse en formato vectorial (SVG) para garantizar escalabilidad. Para implementations web, proporcionar también PNG en múltiples resoluciones.

---

## 6. Sistema de Componentes

### 6.1 Principios de Diseño de Componentes

Los componentes del sistema siguen principios de consistencia visual y funcional:

**Predictibilidad**: Cada componente debe comportarse de la manera que el usuario espera basándose en convenciones established. Un botón parece un botón, una tarjeta tiene bordes y elevación como otras tarjetas.

**Flexibilidad controlada**: Los componentes pueden adaptarse a contextos específicos (como el color del tenant) pero mantienen su estructura fundamental. Las variantes son extensiones controladas, no excepciones arbitrarias.

**Estados completos**: Cada componente interactivo debe tener definido todos sus estados visuales: default, hover, active/pressed, focus, disabled, loading, error.

### 6.2 Botones

Los botones son el elemento principal de llamada a acción. El sistema define estilos para diferentes contextos y jerarquías:

**Botón Primario (CTA principal)**

Utilizado para la acción más importante en cada contexto. Color de fondo en color de acento, texto en blanco, sin borde.

Especificaciones de estilo:

- Background: color de acento definido en paleta
- Color: blanco o color de alto contraste
- Border: ninguno
- Border-radius: 8px (compartido con otros botones)
- Padding: proporcional al tamaño del botón
- Font-size: 13-14px
- Font-weight: 600

**Botón Secundario**

Utilizado para acciones importantes pero no primarias. Fondo transparente con borde en color de acento.

Especificaciones de estilo:

- Background: transparente
- Color: color de acento
- Border: 1.5px solid en color de acento
- Border-radius: 8px
- Padding: igual que botón primario
- Font-size: 13-14px
- Font-weight: 600

**Botón de Contexto Tenant**

Cuando el tenant tiene color de acento personalizado, los botones en su dashboard pueden usar ese color en lugar del color de acento de la aplicación. Implementar mediante variable CSS que permite override.

### 6.3 Estados de Interacción de Botones

**Default**: Estado base del botón según tipo.

**Hover**: El cursor se encuentra sobre el botón. El fondo debe oscurecerse ligeramente (10-15% más oscuro) o cambiar a la versión hover del color. El puntero del cursor cambia a pointer.

**Active/Pressed**: El usuario ha hecho clic y mantiene presionado. El fondo debe oscurecerse más que en hover (20-25% más oscuro). Puede haber un ligero cambio de posición (translateY de 1px) para simular presión física.

**Focus**: El botón tiene foco de teclado (Tab navigation). Mostrar outline visible en color de acento o un anillo de foco claramente perceptible. Este estado es crítico para accesibilidad.

**Disabled**: El botón no es clickeable. Opacidad reducida (50-60%), cursor en not-allowed, sin efecto hover.

**Loading**: Para acciones que requieren tiempo de procesamiento. Mostrar indicador de carga (spinner, skeleton, texto "cargando") y deshabilitar interacción.

### 6.4 Cards de Métricas

Las cards de métricas presentan datos importantes en el dashboard. Deben ser escaneables rápidamente y destacar el valor numérico principal.

Estructura de una card de métrica:

```
┌─────────────────────────┐
│ [Ícono opcional]        │
│                         │
│         1,234           │  ← Valor (grande, color de acento)
│                         │
│  Órdenes totales        │  ← Label (pequeño, color terciario)
│                         │
└─────────────────────────┘
```

Especificaciones de estilo:

- Background: color superficie (blanco)
- Border: 0.5px solid color borde sutil
- Border-radius: 8-10px
- Padding: 12-16px
- Valor: font-size grande (20-24px), font-weight bold, color de acento del tenant
- Label: font-size pequeño (10-11px), color texto terciario, margin-bottom para separación

### 6.5 Badges de Estado

Los badges indican el estado de elementos como órdenes, reservaciones o documentos. Cada estado tiene color de texto y fondo asociado.

**Badge de Éxito (Completado/Entregado)**

- Background: versión pastel del verde de éxito
- Color: verde de éxito (texto oscuro sobre fondo claro)
- Border-radius: pill (20px o más)
- Font-size: 10-11px
- Font-weight: 500
- Padding: 2px 8px

**Badge de Advertencia (En Proceso/Pendiente)**

- Background: versión pastel del ámbar de advertencia
- Color: ámbar de advertencia
- Mismas dimensiones que badge de éxito

**Badge de Error (Cancelado/Rechazado)**

- Background: versión pastel del rojo de error
- Color: rojo de error
- Mismas dimensiones que badge de éxito

**Badge de Información (Neutral/Abierto)**

- Background: versión pastel del azul de información
- Color: azul de información
- Mismas dimensiones que badge de éxito

### 6.6 Avatares

Los avatares representan al tenant o a usuarios dentro del sistema. Deben ser reconocibles y funcionar en diferentes tamaños.

**Avatar de Sidebar (Pequeño)**

- Tamaño: 30×30px
- Border-radius: 7px (cuadrado redondeado)
- Contenido: logo del tenant o iniciales
- Background: color de acento del tenant
- Texto: iniciales en blanco, font-size 11px, font-weight bold

**Avatar de Login (Grande)**

- Tamaño: 52×52px
- Border-radius: 12px
- Contenido: logo del tenant o iniciales
- Background: color de acento del tenant
- Texto: iniciales en blanco, font-size 18px, font-weight 800

### 6.7 Campos de Formulario

Los campos de formulario deben ser claros, con labels visibles y feedback de estado apropiado.

**Estructura estándar de campo:**

```
[ Label                          ]
[ Campo de entrada               ]
[ Mensaje de ayuda o error       ]
```

Especificaciones de estilo:

- Label: font-size 12-13px, font-weight 500, color texto primario, positioned encima del campo
- Campo: height 40-44px, border 1px solid color borde, border-radius 8px, padding horizontal 12px
- Placeholder: color texto terciario
- Mensaje de ayuda: font-size 11px, color texto terciario, debajo del campo
- Focus state: border en color de acento, ring de foco sutil
- Error state: border en color de error, mensaje de error en color de error debajo

### 6.8 Barras de Navegación

La navegación principal del dashboard utiliza un sidebar vertical. Para espacios horizontales o mobile, se implementa navegación alternativa.

**Sidebar de Dashboard**

- Ancho: 180-200px
- Background: color oscuro de la paleta
- Items de navegación: altura 40-44px, icon + label, padding horizontal
- Item activo: background highlight, posible borde izquierdo en color de acento
- Item hover: background ligeramente más claro

**Navbar Mobile**

- Altura: 56px
- Fondo: superficie con borde inferior
- Contenido: menú hamburguesa, logo del tenant centrado o a la derecha
- Navegación expandida: drawer que aparece desde la izquierda con items de navegación

---

## 7. Layout y Espaciado

### 7.1 Sistema de Grid

El sistema utiliza un grid base de 4px o 8px para mantener consistencia en todo el espaciado. Los valores de espaciado son múltiplos de esta unidad base:

| Valor | Uso |
|---|---|
| 4px | Espaciado mínimo, entre elementos relacionados muy cercanamente |
| 8px | Padding interno de elementos pequeños, gaps tight |
| 12px | Padding de cards pequeñas, separación entre elementos relacionados |
| 16px | Padding estándar de cards, separación entre grupos |
| 24px | Separación entre secciones |
| 32px | Padding de secciones en landing |
| 48px | Separación mayor entre secciones |
| 64px | Padding vertical de hero sections |

### 7.2 Border Radius

Los valores de border-radius crean consistencia visual mientras diferencian jerarquías:

| Elemento | Border Radius | Aplicación |
|---|---|---|
| Botones | 8px | Bordes estándar, consistencia |
| Inputs | 8px | Coincide con botones |
| Cards pequeñas | 8-10px | Métricas, elementos de lista |
| Cards principales | 10-12px | Cards de contenido |
| Modales y overlays | 14px | Paneles elevados más pronunciados |
| Avatares | Variable | Sidebar (7px), Login (12px) |

### 7.3 Estructura del Dashboard

El dashboard sigue una estructura de layout definida:

```
┌─────────────────────────────────────────────────────┐
│  Sidebar          │  Área de contenido principal   │
│  (180-200px)      │  (flexible, fundo gris claro)   │
│  Fondo oscuro    │                                  │
│                   │  ┌─────────────────────────────┐ │
│  [Logo] Tenant    │  │ Topbar: saludo + acciones   │ │
│  [Nav items]      │  ├─────────────────────────────┤ │
│                   │  │ Grid de métricas            │ │
│                   │  │                             │ │
│                   │  │ Tabla / contenido principal │ │
│                   │  │                             │ │
│  powered by      │  │                             │ │
│  [Aplicación]     │  │                             │ │
│                   │  └─────────────────────────────┘ │
└─────────────────────────────────────────────────────┘
```

### 7.4 Responsive Strategy

El sistema debe adaptarse a diferentes tamaños de pantalla:

**Desktop (>1024px)**: Layout completo con sidebar visible, grid de métricas en 3-4 columnas.

**Tablet (768-1024px)**: Sidebar colapsable o drawer, grid de métricas en 2 columnas.

**Mobile (<768px)**: Navegación mediante drawer, métricas en stack vertical, tablas con scroll horizontal o reorganización a cards.

---

## 8. Subdominios y URLs

### 8.1 Patrón de URL del Tenant

Cada tenant tiene un subdominio dedicado que sigue el patrón:

```
https://{slug-del-tenant}.{dominio-de-aplicacion}
```

Ejemplos de estructura:

- `burgerscraft.ordamy.co`
- `pizzazeta.ordamy.co`
- `tacosaurora.ordamy.co`

El slug se genera automáticamente desde el nombre del negocio durante el onboarding. Los usuarios pueden personalizar el slug dentro de ciertos límites (caracteres permitidos, disponibilidad).

### 8.2 URLs Especiales

**Landing pública**: URL principal sin subdominio (`ordamy.co` o similar según aplicación).

**Onboarding**: Subdominio de onboarding dedicado o ruta dentro del dominio principal.

**Panel de administración**: Rutas internas que no son accesibles públicamente.

### 8.3 Favicon y Metadatos

Cada aplicación debe tener:

- Favicon que represente la marca
- Meta tags de Open Graph para compartir en redes sociales
- Meta tags de thème-color para navegadores móviles

El tenant no requiere own favicon; utiliza el de la aplicación.

---

## 9. Tono de Comunicación

### 9.1 bigso — Voz Corporativa

bigso habla en contextos institucionales, legales y técnicos. Su voz es:

- **Institucional**: Formal pero accesible, transmite profesionalismo
- **Legal**: Precisa, sin ambigüedad, cumplimiento normativo
- **Técnica**: Clara en documentación, asume competencia técnica del lector

Ejemplos de uso:

- "bigso S.A.S., desarrollador de [Aplicación]"
- En términos y condiciones
- En contactos de soporte técnico
- En documentación de API

### 9.2 La Aplicación — Voz de Producto

La aplicación habla directamente al usuario con una voz empoderadora y orientada al negocio. Su tono es:

- **Directo**: Dice las cosas sin rodeos, acceso rápido a información
- **Empodrador**: Transmite control y capacidad, no impotencia tecnológica
- **Orientado al negocio**: Enfocado en resultados, no en características técnicas
- **Cercano durante onboarding**: Guiado, paso a paso, sin asumir conocimiento previo
- **Aspiracional en marketing**: Prometedor pero concreto, sin jerga técnica innecesaria

Ejemplos de uso:

- "Optimiza y controla tu negocio al máximo"
- "Gestión en una sola plataforma"
- En mensajes de onboarding: guiado con cercanía

### 9.3 El Tenant — Voz en el Sistema

Dentro del panel del tenant, el sistema habla al usuario del tenant en segunda persona directa con tono de negocio. Su voz es:

- **Personal**: Se dirige al negocio del usuario por su nombre
- **Práctico**: Información clara sobre operaciones, sin decoración
- **Proactivo**: Indica cuando hay acciones pendientes o alertas
- **Respetuoso**: Trata al usuario como profesional de su área

Ejemplos de uso:

- "Buenos días, [Nombre del Negocio]"
- "Tu panel está listo"
- "5 órdenes pendientes necesitan atención"
- "3 reservaciones confirmadas para hoy"

El nombre del tenant siempre se muestra con mayúscula inicial como nombre propio, reflejando el respeto por el negocio del usuario.

---

## 10. Estados de Interacción del Sistema

### 10.1 Estados de Carga

Las aplicaciones deben manejar estados de carga de manera que el usuario no sienta incertidumbre:

**Skeleton loading**: Para contenido que tardará en cargar. Mostrar la estructura del contenido con elementos placeholder que simulen la forma del contenido final. No utilizar spinners para bloques de contenido grande.

**Spinner loading**: Para acciones pequeñas como enviar formulario. Spinner simple con texto opcional "Cargando...".

**Progress indicator**: Para procesos que tienen duración estimada. Barra de progreso o porcentaje cuando sea posible.

**Stale-while-revalidate**: Para datos que se actualizan en segundo plano. Mostrar datos existentes mientras se actualizan, sin indicadores de carga si el contenido ya está visible.

### 10.2 Estados de Error

Los errores deben comunicarse de manera útil:

**Error de validación de formulario**: Mostrar mensaje específico junto al campo afectado. No listar todos los errores al inicio; guiar al usuario al primer error.

**Error de conexión**: Mensaje claro que indique el problema y sugiera acción: "No se pudo conectar. Verifica tu conexión a internet."

**Error de servidor (5xx)**: Mensaje que transmita que el problema está en el servidor, no en la acción del usuario. Sugerencia de intentar más tarde.

**Error de autenticación**: Mensaje claro sobre credenciales inválidas o sesión expirada, con acción clara para recuperarla.

### 10.3 Estados Vacíos

Las pantallas vacías deben ser informativas y accionables:

**No hay datos todavía**: Mensaje que explique qué debería aparecer y sugiera crear el primer elemento.

**No hay resultados de búsqueda/filtro**: Mensaje que indique que no hay coincidencias con los filtros activos, con botón para limpiar filtros.

**No hay actividad reciente**: Mensaje de bienvenida para nuevos usuarios o recordatorio suave de que no hay actividad.

---

## 11. Iconografía

### 11.1 Sistema de Iconos

La iconografía debe ser consistente en estilo a través de toda la aplicación. Se recomienda utilizar una fuente de iconos (como Lucide, Heroicons, o Phosphor) que proporcione:

- Trazo consistente
- Variantes filled/outline
- Tamaños que funcionen bien en 16px, 20px, 24px
- Cobertura para iconos de navegación y acciones comunes

### 11.2 Tamaño de Iconos

| Contexto | Tamaño |
|---|---|
| Iconos de navegación sidebar | 20px |
| Iconos en buttons | 16-18px |
| Iconos de status/badge | 14-16px |
| Iconos en inputs | 16px |
| Iconos decorativos | Variable |

### 11.3 Color de Iconos

- Iconos de navegación: color texto sobre fondo de navegación, o blanco sobre fondo oscuro
- Iconos en buttons: color del button (blanco para primary, color accent para secondary)
- Iconos de status: color del estado correspondiente
- Iconos decorativos: color texto terciario o color accent

---

## 12. Animaciones y Transiciones

### 12.1 Principios de Animación

Las animaciones deben mejorar la experiencia sin distraer:

- **Funcionales**: Ayudan a entender发生了什么 y dónde están los elementos
- **Breves**: La mayoría de las transiciones duran 150-300ms
- **Easing natural**: Usar ease-out para entradas, ease-in para salidas
- **Opcionales**: Las animaciones nunca deben ser necesarias para entender el contenido

### 12.2 Transiciones Comunes

| Transición | Duración | Easing | Uso |
|---|---|---|---|
| Fade in/out | 150-200ms | ease-out | Aparición de elementos, modales |
| Slide | 200-300ms | ease-out | Drawers, panels |
| Scale | 150-200ms | ease-out | Botones hover, tooltips |
| Color transition | 100-150ms | linear | Hover states de elementos |

### 12.3 Animaciones de Loading

Spinners y cargadores:

- Usar spinners circulares para acciones breves
- Para flujos largos, mostrar progreso si es posible
- En mobile, preferir animations sutiles para economizar batería

---

## 13. Lo que Nunca se Debe Hacer

### 13.1 Errores de Co-branding

| Evitar | Correcto |
|---|---|
| Mostrar bigso en el dashboard del tenant | Solo en landing y footer legal |
| Ocultar la aplicación completamente en el panel | Siempre aparece como watermark mínimo |
| Usar el logo de la aplicación del mismo tamaño que el del tenant | El tenant es siempre más prominente en su contexto |
| Mezclar los 3 logos en igual jerarquía en una sola pantalla | Máximo 2 marcas visibles con jerarquía clara |
| Escribir "powered by bigso" | Siempre es "powered by [Aplicación]" |

### 13.2 Errores de Color

| Evitar | Correcto |
|---|---|
| Usar color de acento de marca para mensajes de error | Reservar para acciones positivas / CTAs |
| Usar rojo para elementos que no son errores | Reservar rojo para estados de error o cancelación |
| Color de texto con contraste insuficiente | Verificar contraste WCAG AA |
| Mezclar temperaturas de color sin intención | Mantener temperatura consistente o justificar |

### 13.3 Errores de Tipografía

| Evitar | Correcto |
|---|---|
| Usar más de 2-3 familias tipográficas | Una familia con diferentes pesos, o dos complementarias |
| Texto todo en mayúsculas para labels | Capitalización normal o mayúsculas con tracking amplio |
| Usar negrita para todo texto importante | Combinar peso, tamaño y color para jerarquía |
| Tamaño de texto demasiado pequeño para target | Mínimo 14px para texto de contenido, 12px para labels |

### 13.4 Errores de Componentes

| Evitar | Correcto |
|---|---|
| Botones que no tienen todos los estados | Implementar hover, active, focus, disabled |
| Inputs sin labels visibles | Labels siempre presentes, no depender solo de placeholders |
| Cards sin jerarquía clara | Destacar el elemento más importante con tamaño y color |
| Tablas sin consideración mobile | Diseño responsive o alternativas a tabla |

---

## 14. Checklist por Pantalla

### 14.1 Landing Pública

- [ ] Logo de la aplicación visible y prominente en navbar
- [ ] Referencia a bigso discreta junto al logo
- [ ] Sin referencia al tenant
- [ ] Footer con copyright de bigso
- [ ] CTA en color de acento de la aplicación
- [ ] Tipografía de títulos en color oscuro o de acento
- [ ] Fondo en color de fondo cálido definido en paleta

### 14.2 Login Contextual del Tenant

- [ ] Logo/avatar del tenant centrado y prominente
- [ ] Nombre del tenant como elemento principal
- [ ] URL del subdominio visible
- [ ] "Plataforma gestionada por [Aplicación]" en footer del card
- [ ] "un producto de bigso" como segunda línea, visualmente menor
- [ ] Color del botón de login en color de acento (estándar) o del tenant (white-label)

### 14.3 Onboarding

- [ ] Logo de la aplicación en navbar
- [ ] Indicador de progreso "Paso X de Y" visible
- [ ] Sin mencionar bigso hasta el pie de formulario
- [ ] Tono guiado y cercano en labels
- [ ] Color de acento de la aplicación en CTAs
- [ ] Campos de formulario con labels claros y mensajes de ayuda

### 14.4 Dashboard Interno

- [ ] Logo/avatar del tenant en header del sidebar
- [ ] Color de acento del tenant en métricas y CTAs
- [ ] "powered by [Aplicación]" en el pie del sidebar (mínimo, discreto)
- [ ] bigso completamente ausente
- [ ] Saludo personalizado con nombre del tenant
- [ ] Sidebar con navegación clara y estados activos correctos
- [ ] Cards de métricas con valores destacados y labels claros

---

## 15. Tokens de Diseño

### 15.1 Qué son los Tokens

Los tokens de diseño son variables que almacenan valores de diseño (colores, tamaños, espaciados) que se referencian en el código. Permiten cambio centralizado de valores que se propagan a todos los elementos que los utilizan.

### 15.2 Categorías de Tokens

**Tokens de Color**

```
--color-primary (color de acento de marca)
--color-primary-dark (versión oscura para hover)
--color-background (fondo principal)
--color-surface (fondo de tarjetas)
--color-text-primary (texto principal)
--color-text-secondary (texto secundario)
--color-border (bordes)
--color-success (verde de éxito)
--color-warning (ámbar de advertencia)
--color-error (rojo de error)
--color-info (azul de información)
```

**Tokens de Espaciado**

```
--spacing-xs (4px)
--spacing-sm (8px)
--spacing-md (16px)
--spacing-lg (24px)
--spacing-xl (32px)
--spacing-2xl (48px)
```

**Tokens de Tipografía**

```
--font-family-primary
--font-family-secondary
--font-size-xs (10-11px)
--font-size-sm (12-13px)
--font-size-base (14px)
--font-size-lg (16-18px)
--font-size-xl (20-22px)
--font-size-2xl (24-28px)
--font-size-3xl (32+px)
--font-weight-regular
--font-weight-medium
--font-weight-semibold
--font-weight-bold
--font-weight-extrabold
```

**Tokens de Border Radius**

```
--radius-sm (4-6px)
--radius-md (8px)
--radius-lg (10-12px)
--radius-xl (14px)
--radius-full (pill, 999px)
```

### 15.3 Override de Tenant

Para implementaciones white-label, los tokens de color de acento pueden ser overridden:

```
:root {
  --color-accent: var(--ordamy-orange);
  --tenant-accent: var(--ordamy-orange);
}

[data-tenant-accent] {
  --tenant-accent: var(--color-accent);
}
```

O cuando el tenant especifica su color:

```
[data-tenant-accent="#FF5722"] {
  --tenant-accent: #FF5722;
}
```

---

## Anexo: Glosario

**bigso**: La empresa corporativa que desarrolla las aplicaciones del ecosistema.

**Aplicación**: El producto SaaS específico (como ORDAMY) que el mercado adquiere.

**Tenant**: El negocio del cliente que utiliza la plataforma con su propia configuración.

**White-label**: Capacidad de la plataforma para adaptarse visualmente a la marca del tenant.

**Token**: Variable de diseño que almacenan valores reutilizables.

**Sidebar**: Barra de navegación lateral en el dashboard.

**CTA**: Call to Action, elemento que invita al usuario a realizar una acción.

**Dashboard**: Panel principal donde el usuario gestiona su negocio.

---

*Guía elaborada para el equipo de diseño y desarrollo del ecosistema apps by bigso*

*Este documento es la referencia canonical para decisiones de diseño en el ecosistema bigso. Actualizar con cada iteración mayor del sistema de diseño. Las decisiones que se desvíen de esta guía deben documentarse y justificar su razón de ser.*
