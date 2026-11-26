# 🧠 Agent Brain HQ (`hachhyy/agent-brain-hq`)

Repositorio central de arquitectura, **52 skills de IA**, reglas de flujo de trabajo, memoria de código en grafo (**Graphify**), economía de tokens (**Ponytail**) y orquestación de subagentes para desarrollo de aplicaciones en **Antigravity**.

---

## ⚡ Inicialización en 1 Línea (Cualquier Proyecto Pasado o Futuro)

Ejecuta este comando en la raíz de cualquier repositorio para instalar las reglas `.agents/rules/`, el workflow de Graphify, el archivo `skills-lock.json`, las **52 skills** (con el wrapper ligero anti-timeout para `design-taste-frontend`) y el grafo de código AST local (`graphify`):

```bash
curl -fsSL https://raw.githubusercontent.com/hachhyy/agent-brain-hq/main/bootstrap.sh | bash
```

---

## 🏛️ Arquitectura y Reglas de Oro (`.agents/rules/brain.md`)

1. **Claridad total:** Código limpio y directo para que cualquier desarrollador pueda leerlo y entenderlo a la primera.
2. **Revisión previa (Graphify-first):** Antes de crear cualquier archivo, componente o función, se consulta primero el grafo de conocimiento en `graphify-out/graph.json` para reutilizar piezas existentes.
3. **Estructura de carpetas estricta:**
   - `src/pages/`: Solo pantallas completas y rutas.
   - `src/components/`: Piezas visuales agrupadas y reutilizables.
   - `src/data/`: Persistencia de datos (*saving*), llamadas a API/base de datos y autenticación (*logins*).
4. **Un trabajo por archivo (`one job per file`):** Responsabilidad única estricta.
5. **Límite de 300 líneas:** Ningún archivo puede superar las 300 líneas. Al acercarse a 250 líneas, se divide en módulos más pequeños.
6. **Persistencia:** Toda regla nueva acordada se guarda en `.agents/rules/`.

---

## 🤝 Flujo de Trabajo y Reparto de Agentes

| Fase | Agente / Herramienta | Responsabilidad |
| :--- | :--- | :--- |
| **1. Exploración y Memoria** | `graphify` + Subagente `research` | Consultar `graphify-out/graph.json` (`graphify query`, `path`, `explain`) antes de abrir archivos a ciegas. Delegar búsquedas extensas al subagente `research` para mantener limpio el contexto principal. Ejecutar `graphify update .` (AST local, 0 tokens) tras cada edición. |
| **2. Economía de Código y Tokens** | `ponytail` (modo `full`) | El mejor código es el que no hace falta escribir. Realizar el cambio mínimo completo que resuelve el problema real, sin abstracciones prematuras ni sobreingeniería. |
| **3. Planificación y Ejecución Paralela** | `writing-plans` + Subagentes `self` (`dispatching-parallel-agents` / `subagent-driven-development`) | En tareas de >2 archivos, diseñar plan con `writing-plans` antes de tocar código. Repartir subtareas independientes (ej. UI en `src/components/` y lógica en `src/data/`) en subagentes paralelos. |
| **4. Diseño UI/UX Anti-Slop** | `design-taste-frontend`, `impeccable`, `unslop`, `ui-ux-pro-max`, `emilkowalski/skills` | Erradicar diseños genéricos de IA. Aplicar sistemas de diseño con carácter, animaciones con propósito (`animate`, `choreograph`), gestos táctiles (`gestures`) y experiencia nativa móvil (`apple-design`, `mobile-native`). |
| **5. Calidad, Debugging y Revisión** | `systematic-debugging`, `test-driven-development`, `verification-before-completion`, `ponytail-review` | Prohibido parchar a ciegas: ante cualquier fallo se activa `systematic-debugging`. Antes de cerrar tarea, verificar ejecución real y auditar el diff con `ponytail-review`. |

---

## 🧩 Catálogo Completo de las 52 Skills por Categoría

### 1. Memoria de Código y Descubrimiento (2 skills)

| # | Skill | Origen | Propósito |
| :-: | :--- | :--- | :--- |
| 1 | `graphify` | `graphifyy` | Grafo de conocimiento AST local (`graphify-out/graph.json`) con `query`, `path`, `explain` y actualización sin coste de tokens (`graphify update .`). |
| 2 | `find-skills` | `vercel-labs/skills` | Descubrimiento e instalación de nuevas skills del ecosistema abierto. |

### 2. Economía de Código, Auditoría y Deuda Técnica — Ponytail Suite (6 skills)

| # | Skill | Origen | Propósito |
| :-: | :--- | :--- | :--- |
| 3 | `ponytail` | `DietrichGebert/ponytail` | Disciplina de economía de código y tokens (`full` / `lite`): cambios mínimos completos sin código muerto ni abstracciones especulativas. |
| 4 | `ponytail-review` | `DietrichGebert/ponytail` | Revisión del `git diff` buscando líneas innecesarias, helpers redundantes o sobreingeniería antes de hacer commit. |
| 5 | `ponytail-audit` | `DietrichGebert/ponytail` | Auditoría estática del repositorio para detectar archivos sobredimensionados, código duplicado y oportunidades de simplificación. |
| 6 | `ponytail-debt` | `DietrichGebert/ponytail` | Análisis de velocidad y deuda técnica a través del historial de commits y churn de archivos. |
| 7 | `ponytail-gain` | `DietrichGebert/ponytail` | Medición de ahorro de líneas de código y tokens logrados aplicando Ponytail. |
| 8 | `ponytail-help` | `DietrichGebert/ponytail` | Guía rápida de referencia y comandos de la suite Ponytail. |

### 3. Arquitectura, Planificación, Subagentes y Calidad — Superpowers Suite (15 skills)

| # | Skill | Origen | Propósito |
| :-: | :--- | :--- | :--- |
| 9 | `using-superpowers` | `obra/superpowers` | Protocolo base para activar la skill adecuada antes de responder o escribir código. |
| 10 | `brainstorming` | `obra/superpowers` | Exploración de requisitos, intención del usuario y diseño antes de implementar. |
| 11 | `writing-plans` | `obra/superpowers` | Creación de planes de implementación paso a paso para tareas multi-archivo (>2 archivos). |
| 12 | `executing-plans` | `obra/superpowers` | Ejecución estructurada de planes con puntos de control y revisión. |
| 13 | `dispatching-parallel-agents` | `obra/superpowers` | Coordinación de múltiples subagentes en paralelo para tareas independientes sin estado compartido. |
| 14 | `subagent-driven-development` | `obra/superpowers` | Ejecución de planes mediante subagentes especializados por tarea dentro de la sesión. |
| 15 | `systematic-debugging` | `obra/superpowers` | Diagnóstico de causa raíz obligatorio ante cualquier bug o fallo antes de proponer parches. |
| 16 | `test-driven-development` | `obra/superpowers` | Desarrollo guiado por pruebas (Red-Green-Refactor) antes de escribir código de producción. |
| 17 | `verification-before-completion` | `obra/superpowers` | Verificación empírica con comandos y pruebas antes de declarar una tarea completada. |
| 18 | `requesting-code-review` | `obra/superpowers` | Preparación y solicitud de revisión de código al completar features o antes de fusionar. |
| 19 | `receiving-code-review` | `obra/superpowers` | Evaluación técnica rigurosa del feedback de revisión antes de aplicar cambios. |
| 20 | `using-git-worktrees` | `obra/superpowers` | Aislamiento de ramas de desarrollo mediante Git worktrees. |
| 21 | `finishing-a-development-branch` | `obra/superpowers` | Cierre limpio de ramas de desarrollo (merge, PR o limpieza). |
| 22 | `writing-skills` | `obra/superpowers` | Diseño, edición y verificación de nuevas skills reutilizables. |
| 23 | `diagnosing-superpowers` | `obra/superpowers` | Diagnóstico y verificación del estado de instalación de skills y plugins. |

### 4. Diseño UI/UX Anti-Slop, Sistemas de Diseño y Branding (11 skills)

| # | Skill | Origen | Propósito |
| :-: | :--- | :--- | :--- |
| 24 | `design-taste-frontend` | `Leonxlnx/taste-skill` | Suite Senior UI/UX Engineer para arquitectura frontend de alto nivel (con wrapper ligero en `.agents/skills/` y 1,631 assets en `.agents/taste-skill-ref/`). |
| 25 | `impeccable` | `pbakaus/impeccable` | Diseño, crítica, auditoría y pulido integral de interfaces web y móviles, jerarquía, tipografía, color y sistemas de diseño (`DESIGN.md`). |
| 26 | `unslop` | `heydamir/unslop` | Transformación de interfaces con aspecto genérico de IA (*AI slop*) en diseños con identidad propia, corrigiendo espaciado, color, iconografía y copy. |
| 27 | `ui-ux-pro-max` | `ui-ux-pro-max-cli` | Inteligencia de diseño con base local buscable: 79 estilos, 192 paletas por sector, 74 combinaciones tipográficas, 119 guías UX y 22 stacks. |
| 28 | `ui-styling` | `ui-ux-pro-max-cli` | Estilizado moderno y accesible con `shadcn/ui`, Radix UI, Tailwind CSS y temas claro/oscuro. |
| 29 | `design-system` | `ui-ux-pro-max-cli` | Arquitectura de tokens de diseño (3 capas), arquitectura CSS y generación de sistemas de diseño coherentes. |
| 30 | `design` | `ui-ux-pro-max-cli` | Generación de conceptos visuales, logos, iconos, páginas e activos de interfaz. |
| 31 | `brand` | `ui-ux-pro-max-cli` | Identidad verbal y visual de marca, tono de voz y reglas para que el copy nunca suene a IA. |
| 32 | `banner-design` | `ui-ux-pro-max-cli` | Creación de banners para cabeceras, redes sociales y anuncios con exploración de direcciones artísticas. |
| 33 | `slides` | `ui-ux-pro-max-cli` | Presentaciones HTML interactivas con Chart.js, tokens de diseño y estructuras narrativas. |
| 34 | `learn-taste` | `emilkowalski/skills` | Destilación de correcciones de diseño de una sesión en reglas permanentes dentro de `DESIGN.md`. |

### 5. Ingeniería de Diseño, Animaciones, Gestos y Experiencia Nativa — Emil Kowalski Suite (18 skills)

| # | Skill | Origen | Propósito |
| :-: | :--- | :--- | :--- |
| 35 | `emil-design-eng` | `emilkowalski/skills` | Filosofía de Design Engineering de Emil Kowalski: pulido invisible, física natural, velocidad y contención visual. |
| 36 | `animate` | `emilkowalski/skills` | Diseño e implementación de animaciones web con CSS, Motion (Framer Motion) y Web Animations API con curvas y duraciones precisas. |
| 37 | `choreograph` | `emilkowalski/skills` | Coreografía de secuencias multi-elemento: *staggers*, morphing con `layoutId` y transiciones coordinadas. |
| 38 | `gestures` | `emilkowalski/skills` | Interacciones táctiles y de puntero: *drag-to-dismiss*, *rubber-banding*, *velocity projection*, *snap points* y *press feedback*. |
| 39 | `animation-performance` | `emilkowalski/skills` | Optimización a 60/120fps: propiedades de composición GPU, diagnóstico de *jank*, *layout thrashing* y coste de `blur`/filtros. |
| 40 | `animation-vocabulary` | `emilkowalski/skills` | Vocabulario técnico preciso de motion design (*spring*, *damping*, *overshoot*, *stagger*, *FLIP*, *interruptibility*). |
| 41 | `find-animation-opportunities` | `emilkowalski/skills` | Identificación de puntos exactos donde el movimiento aporta comprensión espacial o feedback real. |
| 42 | `improve-animations` | `emilkowalski/skills` | Auditoría de código de animaciones existente y plan priorizado de mejoras de motion. |
| 43 | `review-animations` | `emilkowalski/skills` | Revisión estricta de diffs de animación bajo el listón de calidad de Emil Kowalski. |
| 44 | `remove-animations` | `emilkowalski/skills` | Eliminación de animaciones superfluas en acciones de teclado o superficies de alta frecuencia. |
| 45 | `mobile-native` | `emilkowalski/skills` | Ajustes CSS y meta-tags para que una PWA se sienta 100% nativa en móvil (*safe-area*, *100dvh*, *tap highlight*, *overscroll*). |
| 46 | `apple-design` | `emilkowalski/skills` | Criterios de las Human Interface Guidelines de Apple para iOS, iPadOS y macOS. |
| 47 | `animate-expo` | `emilkowalski/skills` | Animaciones nativas a 120fps en React Native / Expo con Reanimated v4, Gesture Handler y Skia. |
| 48 | `write-swift` | `emilkowalski/skills` | Desarrollo en Swift 6 moderno, concurrencia segura (`@concurrent`, `actors`), tipos por valor y rendimiento ARC. |
| 49 | `prototype` | `emilkowalski/skills` | Construcción de múltiples variantes interactivas de un componente con selector en vivo para elegir la mejor dirección. |
| 50 | `break-ui` | `emilkowalski/skills` | Pruebas de estrés adversariales sobre interfaces (doble clic rápido, pérdida de red, pantallas extremas, *back* durante envío). |
| 51 | `pick-ui-library` | `emilkowalski/skills` | Selección curada de librerías frontend (primitivas, drawers, toasts, command menus, gráficas, virtualización). |
| 52 | `ask-sonner` | `emilkowalski/skills` | Guía arquitectónica y patrones del componente de notificaciones `sonner`. |

---

## 🛡️ Optimización Anti-Timeout para `design-taste-frontend`

La skill `design-taste-frontend` (`Leonxlnx/taste-skill`) incluye **1,631 archivos de referencia**. Para evitar que el indexador de `list_skills` en Antigravity sufra timeouts al escanear miles de archivos en `.agents/skills/`:

1. `bootstrap.sh` mueve automáticamente el contenido completo a `.agents/taste-skill-ref/design-taste-frontend/`.
2. Crea un wrapper ligero en `.agents/skills/design-taste-frontend/SKILL.md` que redirige al agente a `.agents/taste-skill-ref/design-taste-frontend/SKILL.md`.
3. Así `list_skills` responde instantáneamente manteniendo el 100% de los recursos de `taste-skill` accesibles localmente.

---

## 📁 Estructura del Repositorio

```text
.
├── .agents/
│   ├── rules/
│   │   ├── brain.md          # Reglas de Oro, estructura src/ y reparto de agentes
│   │   └── graphify.md       # Regla always_on para consultar el grafo antes de leer archivos
│   └── workflows/
│       └── graphify.md       # Workflow /graphify para construir o actualizar el grafo
├── bootstrap.sh              # Instalador universal de 1 comando para cualquier proyecto
├── skills-lock.json          # Lockfile determinista de skills (Superpowers, Ponytail, Taste, Emil, Impeccable, Unslop)
└── README.md                 # Documentación maestra de arquitectura y catálogo de 52 skills
```
