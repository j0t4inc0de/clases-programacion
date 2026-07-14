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
    title: 'Bases de datos relacionales',
    desc: 'Diseña y consulta tablas estructuradas con SQL. Domina el modelado de datos, claves primarias, foráneas y consultas complejas.',
    icon: 'sql'
  },
  {
    title: 'Bases de datos no relacionales',
    desc: 'Aprende sobre flexibilidad y escalabilidad con NoSQL (MongoDB, clave-valor). Estructura documentos JSON y maneja grandes volúmenes de datos.',
    icon: 'nosql'
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
            
            <img v-else-if="topic.icon === 'python'" src="/python_logo_icon.webp" alt="Python Logo" class="topic-icon python-webp-icon" />
            
            <svg v-else-if="topic.icon === 'sql'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <ellipse cx="12" cy="5" rx="9" ry="3"></ellipse>
              <path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"></path>
              <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"></path>
            </svg>
            
            <svg v-else-if="topic.icon === 'nosql'" class="topic-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <ellipse cx="12" cy="5" rx="9" ry="3"></ellipse>
              <path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"></path>
              <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"></path>
              <path d="M7 16l-2 2 2 2"></path>
              <path d="M17 16l2 2-2 2"></path>
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

.python-webp-icon {
  object-fit: contain;
  transition: transform 0.3s ease;
}

.topic-card:hover .python-webp-icon {
  transform: scale(1.1);
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
