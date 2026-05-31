<script setup>
import { ref } from 'vue'

const steps = ref([
  {
    num: '1',
    title: 'Diagnóstico',
    desc: 'Identificamos qué nivel traes, tus principales dudas y el temario de tu asignatura escolar o universitaria.'
  },
  {
    num: '2',
    title: 'Explicación simple',
    desc: 'Abordamos la teoría con analogías del mundo real y ejemplos sencillos antes de tocar una sola línea de código.'
  },
  {
    num: '3',
    title: 'Práctica guiada',
    desc: 'Escribimos código juntos compartiendo pantalla. Te guío paso a paso para resolver los primeros problemas.'
  },
  {
    num: '4',
    title: 'Práctica autónoma',
    desc: 'Te propongo ejercicios pequeños para que pongas a prueba lo aprendido por tu cuenta mientras estoy en línea.'
  },
  {
    num: '5',
    title: 'Feedback y refuerzo',
    desc: 'Revisamos los errores juntos, despejamos dudas finales y planificamos material complementario para la semana.'
  }
])
</script>

<template>
  <section id="metodo" class="methodology-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">Paso a paso</span>
        <h2 class="section-title">Nuestra Metodología de Clases</h2>
        <p class="section-subtitle">
          Un enfoque estructurado pero flexible que garantiza que entiendas la lógica detrás de cada ejercicio.
        </p>
      </div>

      <div class="timeline-container">
        <!-- Connecting Line background -->
        <div class="timeline-line-bg"></div>

        <div class="steps-grid">
          <div 
            v-for="(step, index) in steps" 
            :key="index" 
            class="step-item"
          >
            <div class="step-num-wrapper">
              <div class="step-num">{{ step.num }}</div>
            </div>
            <div class="step-content glass-panel">
              <h3 class="step-title">Paso {{ step.num }}: {{ step.title }}</h3>
              <p class="step-desc">{{ step.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.methodology-section {
  background-color: var(--bg-secondary);
}

.timeline-container {
  position: relative;
  margin-top: 60px;
}

.timeline-line-bg {
  position: absolute;
  top: 40px;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, var(--accent) 0%, var(--accent-green) 100%);
  z-index: 1;
  opacity: 0.3;
}

.steps-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
  position: relative;
  z-index: 2;
}

.step-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.step-num-wrapper {
  margin-bottom: 24px;
  background-color: var(--bg-secondary);
  padding: 0 10px; /* Gives the illusion of breaking the line */
}

.step-num {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-color: var(--bg-primary);
  border: 3px solid var(--accent);
  color: var(--accent);
  font-family: var(--font-heading);
  font-size: 1.5rem;
  font-weight: 800;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 15px rgba(var(--accent-rgb), 0.2);
  transition: all 0.3s ease;
}

.step-item:hover .step-num {
  background-color: var(--accent);
  color: #ffffff;
  transform: scale(1.1);
  box-shadow: 0 0 20px rgba(var(--accent-rgb), 0.4);
  border-color: var(--accent);
}

/* Alternate colors for steps to make it visually interesting */
.step-item:nth-child(even) .step-num {
  border-color: var(--accent-green);
  color: var(--accent-green);
  box-shadow: 0 0 15px rgba(var(--accent-green-rgb), 0.15);
}

.step-item:nth-child(even):hover .step-num {
  background-color: var(--accent-green);
  color: #ffffff;
  border-color: var(--accent-green);
  box-shadow: 0 0 20px rgba(var(--accent-green-rgb), 0.3);
}

.step-content {
  padding: 24px;
  background-color: var(--bg-primary);
  border: 1px solid var(--border-color);
  height: 100%;
}

.step-content:hover {
  border-color: var(--accent);
}

.step-item:nth-child(even) .step-content:hover {
  border-color: var(--accent-green);
}

.step-title {
  font-size: 1.1rem;
  margin-bottom: 12px;
  color: var(--text-primary);
}

.step-desc {
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

@media (max-width: 992px) {
  .timeline-line-bg {
    display: none;
  }
  .steps-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }
  .step-item {
    flex-direction: row;
    align-items: flex-start;
    text-align: left;
    gap: 20px;
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
  }
  .step-num-wrapper {
    margin-bottom: 0;
    padding: 0;
  }
  .step-content {
    flex-grow: 1;
  }
}
</style>
