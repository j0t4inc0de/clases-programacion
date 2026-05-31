<script setup>
import { ref } from 'vue'

const topics = ref([
  {
    title: 'Introducción a la programación',
    desc: 'Entiende cómo piensa una computadora y aprende los fundamentos esenciales para resolver cualquier problema lógico.',
    icon: 'code'
  },
  {
    title: 'PSeInt (Pseudocódigo)',
    desc: 'La herramienta ideal para comenzar. Aprende a programar en español sin preocuparte por la sintaxis compleja.',
    icon: 'terminal'
  },
  {
    title: 'Python básico',
    desc: 'Domina el lenguaje más popular y demandado del mundo. Escribe código limpio, legible y muy potente.',
    icon: 'python'
  },
  {
    title: 'Variables, condicionales y ciclos',
    desc: 'Aprende a estructurar decisiones (si/entonces) y repeticiones (ciclos para/mientras) en tus algoritmos.',
    icon: 'branch'
  },
  {
    title: 'Funciones',
    desc: 'Divide y vencerás. Aprende a modularizar tu código para crear programas limpios, reutilizables y profesionales.',
    icon: 'function'
  },
  {
    title: 'Preparación para pruebas',
    desc: 'Repasa con anticipación el temario exacto de tu ramo, resuelve certámenes pasados y asegura tu aprobación.',
    icon: 'academic'
  },
])
</script>

<template>
  <section id="aprender" class="learn-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">Temario & Apoyo</span>
        <h2 class="section-title">¿Qué puedes aprender en mis clases?</h2>
        <p class="section-subtitle">
          Desde los primeros pasos lógicos hasta la resolución de guías complejas y preparación de exámenes universitarios.
        </p>
      </div>

      <div class="topics-grid">
        <div 
          v-for="(topic, index) in topics" 
          :key="index" 
          class="topic-card glass-panel"
        >
          <div class="topic-icon-wrapper">
            <!-- Render custom inline SVG icons depending on the identifier -->
            <svg v-if="topic.icon === 'code'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="16 18 22 12 16 6"></polyline>
              <polyline points="8 6 2 12 8 18"></polyline>
            </svg>
            
            <svg v-else-if="topic.icon === 'terminal'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="4 17 10 11 4 5"></polyline>
              <line x1="12" y1="19" x2="20" y2="19"></line>
            </svg>
            
            <svg v-else-if="topic.icon === 'python'" class="topic-icon python-colored" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
              <path d="M11.93 2.01c-2.45.02-4.71.69-5.91 1.83C4.38 5.43 4.54 7.29 4.54 8.78h4.54c1.23 0 2.22.99 2.22 2.22v4.54c0 1.23-.99 2.22-2.22 2.22H3.72c-.89 0-1.78-.11-2.45-.67-.78-.67-.93-1.63-.93-2.61V8.78c0-2.46.68-4.72 1.82-5.91C3.81 1.15 6.07.49 8.52.49h3.41c1.37 0 2.45.1 3.41.67.68.45.98 1.15.98 1.83v2.01h-4.38c-.78 0-1.42.64-1.42 1.42v1.41h4.38V4.54c0-.98-.16-1.93-.93-2.6-1.12-1.01-3.21-1.92-5.93-1.93zM5.96 5.86a.91.91 0 1 1 0 1.82.91.91 0 0 1 0-1.82zm8.56 16.13c2.45-.02 4.71-.69 5.91-1.83 1.64-1.59 1.48-3.45 1.48-4.94h-4.54c-1.23 0-2.22-.99-2.22-2.22v-4.54c0-1.23.99-2.22 2.22-2.22h5.36c.89 0 1.78.11 2.45.67.78.67.93 1.63.93 2.61v5.7c0 2.46-.68 4.72-1.82 5.91-1.65 1.72-3.91 2.38-6.36 2.38h-3.41c-1.37 0-2.45-.1-3.41-.67-.68-.45-.98-1.15-.98-1.83v-2.01h4.38c.78 0 1.42-.64 1.42-1.42v-1.41h-4.38v3.29c0 .98.16 1.93.93 2.6 1.12 1.01 3.21 1.92 5.93 1.93zm5.97-3.26a.91.91 0 1 1 0-1.82.91.91 0 0 1 0 1.82z"/>
            </svg>
            
            <svg v-else-if="topic.icon === 'branch'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <line x1="6" y1="3" x2="6" y2="15"></line>
              <circle cx="18" cy="6" r="3"></circle>
              <circle cx="6" cy="18" r="3"></circle>
              <path d="M18 9a9 9 0 0 1-9 9"></path>
            </svg>
            
            <svg v-else-if="topic.icon === 'function'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
              <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
              <text x="9" y="13" font-family="monospace" font-weight="bold" font-size="8" fill="currentColor">f(x)</text>
            </svg>
            
            <svg v-else-if="topic.icon === 'academic'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M22 10v6M2 10l10-5 10 5-10 5z"></path>
              <path d="M6 12v5c0 2 2 3 6 3s6-1 6-3v-5"></path>
            </svg>
            
            <svg v-else class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
              <polyline points="14 2 14 8 20 8"></polyline>
              <line x1="16" y1="13" x2="8" y2="13"></line>
              <line x1="16" y1="17" x2="8" y2="17"></line>
              <polyline points="10 9 9 9 8 9"></polyline>
            </svg>
          </div>
          
          <h3 class="topic-card-title">{{ topic.title }}</h3>
          <p class="topic-card-desc">{{ topic.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.learn-section {
  background-color: var(--bg-primary);
}

.topics-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
}

.topic-card {
  padding: 30px;
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  height: 100%;
}

.topic-card:hover {
  transform: translateY(-5px);
  border-color: var(--accent);
  box-shadow: 0 15px 30px rgba(var(--accent-rgb), 0.1);
}

.topic-icon-wrapper {
  background-color: var(--bg-tertiary);
  width: 54px;
  height: 54px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  color: var(--accent);
  border: 1px solid var(--border-color);
  transition: all 0.3s ease;
}

.topic-card:hover .topic-icon-wrapper {
  background-color: var(--accent);
  color: #ffffff;
  transform: scale(1.05);
}

.topic-icon {
  width: 26px;
  height: 26px;
}

.python-colored {
  transition: fill 0.3s ease;
}

.topic-card:hover .python-colored {
  fill: #ffffff;
}

.topic-card-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 12px;
  color: var(--text-primary);
}

.topic-card-desc {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

/* Center card if it is the 7th odd element on large screens */
@media (min-width: 992px) {
  .topics-grid > .topic-card:nth-child(7) {
    grid-column: span 1;
  }
}
</style>
