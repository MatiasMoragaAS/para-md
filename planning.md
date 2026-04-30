# Planificación del Proyecto - Apocalipsis 25

## Integrantes del Grupo
- [Nombre Integrante 1] - [Rol: Líder técnico / Frontend]
- [Nombre Integrante 2] - [Rol: Lógica de juego / JavaScript]
- [Nombre Integrante 3] - [Rol: Diseño visual / CSS]
- [Nombre Integrante 4] - [Rol: Testing / Documentación]

## Repositorio GitHub
[Enlace al repositorio]

## Tecnologías Principales
- **Framework:** Vue.js 3 (Composition API)
- **Estado global:** Pinia
- **Build tool:** Vite
- **Estilos:** NES.css + Pixelium Design
- **Testing:** Vitest
- **CI/CD:** GitHub Actions
- **Docker:** Containerización

---

## Semana 1 – Diseño y Planificación

### 📋 Tareas planificadas:

**Antes de escribir código:**
- [ ] Crear repositorio en GitHub con `.gitignore` (node_modules, dist, .env)
- [ ] Invitar a todos los integrantes al repositorio
- [ ] Configurar ramas: `main`, `develop`, `feature/*`

**Documentación:**
- [ ] Redactar `DESIGN.md` completo con:
  - Mockups de pantallas principales:
    - Pantalla de inicio (Día 0 - Noticia en TV)
    - Pantalla de juego (estadísticas + área de decisiones)
    - Pantalla de Game Over
    - Pantalla de Victoria (rescate en helicóptero)
  - Justificación del framework elegido (Vue.js 3 + Pinia)
    - *Por qué Vue.js: Reactividad nativa, fácil manejo de estado con Pinia, comunidad grande, ideal para UI interactiva*
  - Estructura de carpetas propuesta (ver abajo)
  - Descripción del juego: mecánicas, reglas, flujo
- [ ] Redactar `PLANNING.md` inicial con este cronograma
- [ ] Crear `README.md` base

**Diseño visual preliminar:**
- [ ] Elegir paleta de colores retro (verdes militares, grises, amarillos cálidos)
- [ ] Seleccionar tipografías: `Press Start 2P` + `VT323`
- [ ] Definir assets necesarios (imágenes pixel art para fondos)

### 🎯 Objetivo de la semana:
> Tener base documental completa, repositorio configurado y diseño visual definido antes del fin de semana.

### 📁 Estructura de carpetas propuesta:
```text
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
```

### ✅ Lo que se logró completar:
*(Se llena al final de la semana)*

### ❌ Lo que NO se logró:
*(Se llena al final de la semana)*

### 📝 Notas:
*(Problemas encontrados, soluciones, cambios de plan)*

---

## Semana 2 – Configuración y Primeros Componentes

### 📋 Tareas planificadas:

**Configuración del proyecto:**
- [ ] Inicializar proyecto Vue.js 3 con Vite:
```
  npm create vue@latest apocalipsis25
  cd apocalipsis25
  npm install
```

-Instalar dependencias principales:
```
npm install pinia
npm install nes.css
npm install @mmt817/pixel-ui
npm install -D vitest @vue/test-utils jsdom
```
-Configurar Vue Router (aunque sea simple, por escalabilidad)

-Configurar vite.config.js para alias y assets

Componentes base:

-Crear main.js con configuración de Pinia

-Crear App.vue con estructura principal (contenedor 16:9)

-Implementar componente StatBar.vue (comida, agua, salud, moral + día)

-Implementar componente PixelBackground.vue (fondo dinámico)

-Implementar estilos base con efecto CRT (scanlines + vignette)

Docker:
-Crear Dockerfile inicial:
```
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5173
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]
```
🎯 Objetivo de la semana:
Proyecto ejecutable en navegador con pantalla inicial, estadísticas visibles y fondos dinámicos funcionando.

✅ Lo que se logró completar:
(Se llena al final de la semana)

❌ Lo que NO se logró:
(Se llena al final de la semana)

📝 Notas:
(Problemas encontrados, soluciones, cambios de plan)

## Semana 3 – Desarrollo de Mecánicas y Lógica del Juego
📋 Tareas planificadas:
Estado global (Pinia):

Implementar gameStore.js con:

-State: day, food, water, health, moral, allowedWoman, gameOver, victory

-Getters: isAlive, displayDay, isHungry

-Actions: applyDecision, consumeDaily, checkGameStatus, resetGame

Sistema de eventos por día:

Crear events.js con array de objetos para cada día:
```
export const events = {
  0: { text: "...", location: "casa", options: [...] },
  1: { text: "...", location: "casa", options: [...] },
  // ... hasta día 25
}
```
Implementar días especiales:

Día 0: Introducción + noticia TV

Día 1: Decisión moral (mujer e hijo)

Día 3: Decisión comida (buscar vs podrida)

Día 5: Medicina (+28 salud)

Día 8: Manual primeros auxilios

Día 12: Cooperación con refugiados

Día 17: Ataque de saqueadores

Día 22: Señal de radio

Día 25: Victoria

Eventos aleatorios:

-Implementar sistema de eventos aleatorios para días sin evento fijo

-Crear 6-8 eventos genéricos (positivos, negativos, neutrales)

Componentes interactivos:

-Implementar StoryText.vue con efecto máquina de escribir

-Implementar sistema de avance por clic/tecla ESPACIO

-Implementar DecisionButtons.vue (botones dinámicos)

🎯 Objetivo de la semana:
Juego completamente jugable del día 0 al día 25, con todas las decisiones afectando recursos y mostrando consecuencias.

✅ Lo que se logró completar:
(Se llena al final de la semana)

❌ Lo que NO se logró:
(Se llena al final de la semana)

📝 Notas:
(Problemas encontrados, soluciones, cambios de plan)

## Semana 4 – Testing y CI/CD
📋 Tareas planificadas:
Pruebas unitarias (Vitest):

-Configurar Vitest en vite.config.js

-Implementar pruebas para gameStore.js:

  -Verificar que applyDecision modifica recursos correctamente

  -Verificar que consumeDaily funciona con/without refugiados

  -Verificar que checkGameStatus detecta game over y victoria

  -Verificar que resetGame vuelve al estado inicial

-Implementar pruebas para componentes:

  -StatBar.vue: verificar que muestra valores correctos

  -DecisionButtons.vue: verificar que emite eventos

GitHub Actions (CI/CD):

-Crear workflow de Linter (.github/workflows/lint.yml):
-Crear workflow de Testing (.github/workflows/test.yml):

DockerHub:

-Crear workflow de Build y Push a DockerHub (.github/workflows/docker.yml):

-Configurar secrets en GitHub (DOCKER_USERNAME, DOCKER_TOKEN)

#Sonido (opcional):

Implementar useAudio.js con Web Audio API

Añadir sonidos: click, damage, victory, game over

🎯 Objetivo de la semana:
Flujo CI/CD funcionando con cada push: linter → pruebas → build Docker → push a DockerHub.

✅ Lo que se logró completar:
(Se llena al final de la semana)

❌ Lo que NO se logró:
(Se llena al final de la semana)

📝 Notas:
(Problemas encontrados, soluciones, cambios de plan)

## Semana 5 – Pulido, Minijuegos y Entrega Final
📋 Tareas planificadas:
Mejoras UI/UX:

Añadir animaciones de transición entre días

Mejorar feedback visual al tomar decisiones

Implementar efecto de partículas (polvo, lluvia opcional)

Asegurar responsividad en móviles (media queries)

Probar en navegadores: Chrome, Firefox, Edge

Minijuegos (opcional - extra crédito):

Implementar minijuego Día 3: Buscar latas en supermercado

-Canvas de 600x400

-3 latas escondidas en 15 segundos

-Click en objeto incorrecto resta tiempo

Implementar minijuego Día 12: Atrapar gotas de lluvia

-Mover balde con mouse

-Atrapar 20 gotas en 20 segundos

Documentación final:

-Completar README.md con:

-Instrucciones de instalación local

-Instrucciones para ejecutar con Docker

-Capturas de pantalla del juego

-Link a GitHub Pages (demo)

-Revisar y actualizar DESIGN.md con decisiones finales

-Revisar y completar PLANNING.md con resultados de todas las semanas

Despliegue:

-Configurar GitHub Pages para demo estática

-Probar que el juego funciona correctamente

-Verificar que no hay errores en consola

Entrega:

Enviar correo al profesor con:

-Nombres de integrantes

-Link al repositorio GitHub

-Link a GitHub Pages

-Link a DockerHub (si aplica)

🎯 Objetivo de la semana:
Proyecto robusto, documentado, testeado y entregado. Versión final jugable y profesional.

✅ Lo que se logró completar:
(Se llena al final de la semana)

❌ Lo que NO se logró:
(Se llena al final de la semana)

📝 Notas:
(Problemas encontrados, soluciones, cambios de plan)
