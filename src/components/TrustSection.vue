<script setup>
import { ref } from 'vue'

const values = ref([
  {
    title: 'Material adaptado al nivel',
    desc: 'Diseñamos explicaciones, ejercicios y retos complementarios a la medida de tus necesidades reales de aprendizaje.',
    highlight: 'Material adaptado al nivel del estudiante',
    icon: 'gear'
  },
  {
    title: 'Enfoque en entender la lógica',
    desc: 'No dictamos código ni resolvemos tareas de forma ciega. Nos enfocamos en enseñarte a razonar y estructurar soluciones por ti mismo.',
    highlight: 'Clases enfocadas en entender la lógica, no solo copiar código',
    icon: 'brain'
  },
  {
    title: 'Acompañamiento paso a paso',
    desc: 'Explicamos con calma y sin prisas. Resolvemos cada duda hasta que el concepto quede completamente claro y consolidado.',
    highlight: 'Acompañamiento paso a paso',
    icon: 'step'
  },
  {
    title: 'Preparación para evaluaciones',
    desc: 'Llegarás al examen con la tranquilidad de haber practicado con ejercicios reales y simulacros enfocados en tu programa.',
    highlight: 'Preparación para evaluaciones',
    icon: 'star'
  }
])
</script>

<template>
  <section class="trust-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">¿Por qué elegir mis clases?</span>
        <h2 class="section-title">Valores que marcan la diferencia</h2>
        <p class="section-subtitle">
          El objetivo no es memorizar sintaxis, sino desarrollar un pensamiento algorítmico estructurado que te sirva para toda la vida.
        </p>
      </div>

      <div class="values-grid">
        <div 
          v-for="(val, index) in values" 
          :key="index" 
          class="value-card glass-panel"
        >
          <div class="value-card-header">
            <div class="value-icon-box">
              <svg v-if="val.icon === 'gear'" class="value-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
              
              <svg v-else-if="val.icon === 'brain'" class="value-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
              </svg>
              
              <svg v-else-if="val.icon === 'step'" class="value-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
              </svg>
              
              <svg v-else class="value-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            
            <h3 class="value-title">{{ val.title }}</h3>
          </div>

          <blockquote class="value-highlight">
            "{{ val.highlight }}"
          </blockquote>

          <p class="value-description">
            {{ val.desc }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.trust-section {
  background-color: var(--bg-secondary);
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
  gap: 30px;
}

.value-card {
  padding: 36px;
  background-color: var(--bg-primary);
  border: 1px solid var(--border-color);
  display: flex;
  flex-direction: column;
  transition: all 0.3s ease;
}

.value-card:hover {
  transform: translateY(-2px);
  border-color: var(--accent);
  box-shadow: 0 10px 25px rgba(var(--accent-rgb), 0.08);
}

.value-card-header {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 20px;
}

.value-icon-box {
  background-color: var(--accent-glow);
  color: var(--accent);
  width: 48px;
  height: 48px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(var(--accent-rgb), 0.15);
  flex-shrink: 0;
  transition: all 0.3s ease;
}

.value-card:hover .value-icon-box {
  background-color: var(--accent);
  color: #ffffff;
}

.value-icon {
  width: 24px;
  height: 24px;
}

.value-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--text-primary);
}

.value-highlight {
  font-size: 1rem;
  font-weight: 600;
  font-style: italic;
  color: var(--accent);
  border-left: 3px solid var(--accent);
  padding-left: 12px;
  margin-bottom: 16px;
  line-height: 1.4;
  transition: all 0.3s ease;
}

.value-card:hover .value-highlight {
  color: var(--accent);
  border-left-color: var(--accent);
}

.value-description {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.6;
}

@media (max-width: 992px) {
  .values-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 576px) {
  .value-card {
    padding: 24px;
  }
  .value-card-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 12px;
  }
}
</style>
