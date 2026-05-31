<script setup>
import { ref } from 'vue'

const targets = ref([
  {
    title: 'Estudiantes de colegio',
    situation: 'Tienen informática o tecnología en el colegio y se topan por primera vez con PSeInt o algoritmos simples.',
    solution: 'Explicamos con juegos y ejemplos prácticos para que lo vean como un desafío divertido, no como una carga.',
    icon: 'backpack'
  },
  {
    title: 'Estudiantes de 1er año de educación superior',
    situation: 'Entraron a Ingeniería, Técnico o Analista Programador y el ramo de "Introducción a la Programación" o "Algoritmos" los tiene sobrepasados.',
    solution: 'Nivelamos los conocimientos, repasamos la materia de cátedra y resolvemos guías oficiales de tu casa de estudios.',
    icon: 'academic'
  },
  {
    title: 'Personas desde cero',
    situation: 'Quieren aprender a programar por interés personal, desarrollo profesional o reconversión laboral pero no saben por dónde empezar.',
    solution: 'Construimos cimientos sólidos. Aprendes lógica pura antes de enredarte con la sintaxis de lenguajes complejos.',
    icon: 'leaf'
  },
  {
    title: 'Alumnos frustrados con la lógica',
    situation: 'Entienden el código cuando lo ven resuelto, pero al enfrentarse a una pantalla en blanco no saben cómo escribir la primera línea.',
    solution: 'Desglosamos el problema en partes pequeñas mediante pseudocódigo, diagramas y técnicas estructuradas de resolución.',
    icon: 'alert'
  },
  {
    title: 'Preparación para pruebas',
    situation: 'Tienen un certamen encima o un examen de recuperación pronto y necesitan entender toda la materia en tiempo récord.',
    solution: 'Sesiones intensivas enfocadas en resolver pruebas pasadas, identificar patrones comunes de examen y maximizar puntaje.',
    icon: 'clock'
  }
])
</script>

<template>
  <section class="target-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">¿Para quién es?</span>
        <h2 class="section-title">¿Estas clases son para ti?</h2>
        <p class="section-subtitle">
          Apoyo adaptado tanto a estudiantes de educación superior, escolares y autodidactas.
        </p>
      </div>

      <div class="targets-container">
        <div 
          v-for="(target, index) in targets" 
          :key="index" 
          class="target-card glass-panel"
        >
          <div class="target-icon-wrapper">
            <svg v-if="target.icon === 'backpack'" class="target-icon-svg" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.168.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.168.477-4.5 1.253" />
            </svg>
            <svg v-else-if="target.icon === 'academic'" class="target-icon-svg" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 14l9-5-9-5-9 5 9 5zm0 0l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14zm-4 6v-7.5l4-2.222" />
            </svg>
            <svg v-else-if="target.icon === 'leaf'" class="target-icon-svg" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
            </svg>
            <svg v-else-if="target.icon === 'alert'" class="target-icon-svg" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <svg v-else class="target-icon-svg" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
          </div>
          <div class="target-body">
            <h3 class="target-card-title">{{ target.title }}</h3>
            <div class="target-context">
              <span class="context-label">Tu situación:</span>
              <p class="context-desc">{{ target.situation }}</p>
            </div>
            <div class="target-solution">
              <span class="solution-label">Cómo lo resolvemos:</span>
              <p class="solution-desc">{{ target.solution }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.target-section {
  background-color: var(--bg-primary);
}

.targets-container {
  display: flex;
  flex-direction: column;
  gap: 24px;
  max-width: 900px;
  margin: 0 auto;
}

.target-card {
  display: flex;
  gap: 24px;
  padding: 30px;
  background: var(--glass-bg);
  border: 1px solid var(--border-color);
  align-items: flex-start;
}

.target-card:hover {
  transform: translateY(-2px);
  border-color: var(--accent);
  box-shadow: 0 10px 25px rgba(var(--accent-rgb), 0.08);
}

.target-icon-wrapper {
  background-color: var(--bg-secondary);
  color: var(--accent);
  width: 70px;
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 16px;
  border: 1px solid var(--border-color);
  flex-shrink: 0;
  transition: all 0.3s ease;
}

.target-card:hover .target-icon-wrapper {
  background-color: var(--accent);
  color: #ffffff;
}

.target-icon-svg {
  width: 32px;
  height: 32px;
}

.target-body {
  flex-grow: 1;
}

.target-card-title {
  font-size: 1.4rem;
  margin-bottom: 16px;
  color: var(--text-primary);
}

.target-context, .target-solution {
  margin-bottom: 12px;
}

.target-solution {
  margin-bottom: 0;
}

.context-label, .solution-label {
  display: inline-block;
  font-size: 0.75rem;
  text-transform: uppercase;
  font-weight: 750;
  padding: 2px 8px;
  border-radius: 4px;
  margin-bottom: 4px;
}

.context-label {
  background-color: rgba(239, 68, 68, 0.1);
  color: #ef4444;
}

.solution-label {
  background-color: rgba(16, 185, 129, 0.1);
  color: var(--accent-green);
}

.context-desc, .solution-desc {
  font-size: 0.95rem;
  line-height: 1.5;
}

.context-desc {
  color: var(--text-secondary);
}

.solution-desc {
  color: var(--text-primary);
}

@media (max-width: 576px) {
  .target-card {
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 16px;
  }
  
  .target-icon-wrapper {
    width: 60px;
    height: 60px;
  }
  
  .context-label, .solution-label {
    margin-left: auto;
    margin-right: auto;
  }
}
</style>
