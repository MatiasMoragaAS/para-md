# Documento de Diseño - [Nombre del Juego]

## Integrantes del Grupo
- [Nombre Integrante 1] - [Rol: Líder técnico / Frontend]
- [Nombre Integrante 2] - [Rol: Lógica de juego / JavaScript]
- [Nombre Integrante 3] - [Rol: Diseño visual / CSS]
- [Nombre Integrante 4] - [Rol: Testing / Documentación]

## Repositorio GitHub
[Enlace al repositorio]

---
## Descripción del juego:

### Contexto:
Tras el estallido de una Tercera Guerra Mundial, múltiples potencias lanzaron ataques nucleares que devastaron gran parte del planeta. Las ciudades quedaron reducidas a ruinas, el aire se volvió peligroso de respirar y los recursos básicos comenzaron a escasear rápidamente. La mayoría de la población no sobrevivió.
En este nuevo mundo, los pocos sobrevivientes deben refugiarse en estructuras improvisadas para resistir las condiciones extremas del entorno: radiación, contaminación, enfermedades y la constante amenaza de otros humanos desesperados.
El jugador asume el rol de un sobreviviente que ha logrado resguardarse en un refugio, dependiendo de qué lugar elija, la dificultad y los recursos varían, Desde allí, deberá tomar decisiones críticas día a día para mantenerse con vida, administrar recursos limitados como comida, agua y suministros médicos, y enfrentar eventos impredecibles que pondrán a prueba su juicio y moral.
Cada decisión tendrá consecuencias, y no siempre existirá una opción correcta. El objetivo es sobrevivir la mayor cantidad de días posible con un límite de 15 días para la victoria
Mecánicas: El juego se basa en un sistema de supervivencia por días, donde el jugador debe tomar decisiones estratégicas tras cada evento que suceda para mantenerse con vida y administrar sus suministros hasta el día 15. Cada evento puede traer beneficios o provocar perdidas, los recursos que se deben administrar es la comida, agua, salud y moral, que van restando cada día y según las decisiones que tomes Si tu salud llega a 0 pierdes, el resto de los recursos si llegan a 0, la vida bajara cada día hasta que la salud llegue a 0, por eso es importante tener siempre comida, agua y moral.

---
## 1. Mockups de Pantallas Principales

### Pantalla 1: Inicio / Día 0 (Noticia en TV)

### Pantalla 2: Juego (Día con Decisión)

### Pantalla 3: Minijuego (Buscar Latas)

### Pantalla 4: Game Over

### Pantalla 5: Victoria (Día 25 - Rescate)



---

## 2. Especificaciones de Tecnología

### Framework elegido: **Vue.js 3 + Pinia**

**Justificación:**

| Criterio | Justificación |
|----------|----------------|
| **Reactividad nativa** | Los cambios en recursos (comida, agua, salud) actualizan automáticamente la UI sin código adicional |
| **Pinia para estado global** | Ideal para manejar el estado del juego (día, recursos, decisiones) de forma centralizada |
| **Composition API** | Permite organizar la lógica por funcionalidad (useAudio, useTypingEffect) |
| **Comunidad y documentación** | Gran soporte, fácil encontrar soluciones a problemas comunes |
| **Curva de aprendizaje** | Más suave que React, ideal para proyectos académicos |
| **Rendimiento** | Virtual DOM eficiente, ideal para UI interactiva |
| **Obligatorio** | El proyecto requiere explícitamente el uso de Vue.js |

**Alternativas descartadas:**
- **React:** Más boilerplate, estado global más complejo (Redux vs Pinia)
- **Svelte:** Menos comunidad, menos recursos educativos
- **Vanilla JS:** Mucho código manual, difícil de mantener

### Estructura de carpetas propuesta:

Proyecto/
├── index.html
├── package.json
├── vite.config.js
├── Dockerfile
├── .gitignore
├── .github/
│ └── workflows/
│ ├── lint.yml
│ └── test.yml
├── src/
│ ├── main.js
│ ├── App.vue
│ ├── components/
│ │ ├── StatBar.vue
│ │ ├── StoryText.vue
│ │ ├── DecisionButtons.vue
│ │ ├── PixelBackground.vue
│ │ └── minigames/
│ │ ├── FindCansGame.vue
│ │ └── CatchRainGame.vue
│ ├── stores/
│ │ └── gameStore.js
│ ├── composables/
│ │ ├── useAudio.js
│ │ └── useTypingEffect.js
│ ├── data/
│ │ └── events.js
│ ├── assets/
│ │ ├── images/
│ │ └── styles/
│ └── tests/
│ └── gameStore.spec.js
└── public/
└── sounds/



### Dependencias principales:

| Dependencia | Versión | Propósito |
|-------------|---------|-----------|
| `vue` | ^3.3.0 | Framework principal |
| `pinia` | ^2.1.0 | Estado global |
| `nes.css` | ^2.3.0 | Framework visual retro (NES) |
| `@mmt817/pixel-ui` | ^1.0.0 | Componentes pixel art para Vue |
| `vite` | ^4.4.0 | Build tool |
| `vitest` | ^0.34.0 | Testing unitario |
| `@vue/test-utils` | ^2.4.0 | Utilidades para testing de Vue |
| `jsdom` | ^22.1.0 | DOM para pruebas |

### Frameworks Visuales Recomendados:

#### **NES.css** - Framework CSS estilo Nintendo NES
```css
@import 'nes.css/css/nes.min.css';
```
Componentes útiles:

- nes-container - Contenedores estilo retro

- nes-btn - Botones 8-bit

- nes-icon heart - Iconos de corazón

- nes-progress - Barras de progreso

Pixelium Design - Componentes pixel art para Vue 3:

Componentes útiles:

- px-card - Tarjetas con borde pixel

- px-button - Botones con efecto click

- px-progress - Barras de estadísticas

Google Fonts (tipografía retro):

```
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323&display=swap" rel="stylesheet">
```
















Descripción del juego:

Contexto: Tras el estallido de una Tercera Guerra Mundial, múltiples potencias lanzaron ataques nucleares que devastaron gran parte del planeta. Las ciudades quedaron reducidas a ruinas, el aire se volvió peligroso de respirar y los recursos básicos comenzaron a escasear rápidamente. La mayoría de la población no sobrevivió.
En este nuevo mundo, los pocos sobrevivientes deben refugiarse en estructuras improvisadas para resistir las condiciones extremas del entorno: radiación, contaminación, enfermedades y la constante amenaza de otros humanos desesperados.
El jugador asume el rol de un sobreviviente que ha logrado resguardarse en un refugio, dependiendo de qué lugar elija, la dificultad y los recursos varían, Desde allí, deberá tomar decisiones críticas día a día para mantenerse con vida, administrar recursos limitados como comida, agua y suministros médicos, y enfrentar eventos impredecibles que pondrán a prueba su juicio y moral.
Cada decisión tendrá consecuencias, y no siempre existirá una opción correcta. El objetivo es sobrevivir la mayor cantidad de días posible con un límite de 15 días para la victoria
Mecánicas: El juego se basa en un sistema de supervivencia por días, donde el jugador debe tomar decisiones estratégicas tras cada evento que suceda para mantenerse con vida y administrar sus suministros hasta el día 15. Cada evento puede traer beneficios o provocar perdidas, los recursos que se deben administrar es la comida, agua, salud y moral, que van restando cada día y según las decisiones que tomes Si tu salud llega a 0 pierdes, el resto de los recursos si llegan a 0, la vida bajara cada día hasta que la salud llegue a 0, por eso es importante tener siempre comida, agua y moral
