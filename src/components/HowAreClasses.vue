<script setup>
import { ref } from 'vue'

const features = ref([
  {
    title: 'Diagnóstico inicial',
    desc: 'Evaluamos tus conocimientos previos en la primera sesión para identificar vacíos lógicos y diseñar la mejor ruta.',
    icon: 'search'
  },
  {
    title: 'Explicación paso a paso',
    desc: 'Nada de tecnicismos complejos o atajos. Explicamos cada concepto desde cero, usando analogías sencillas de la vida diaria.',
    icon: 'map'
  },
  {
    title: 'Material personalizado',
    desc: 'Apuntes de resumen, diagramas de flujo y hojas de ruta diseñados exclusivamente para lo que tú necesitas aprender.',
    icon: 'document'
  },
  {
    title: 'Ejercicios guiados',
    desc: 'Escribimos código juntos. Primero te muestro cómo resolverlo, luego lo hacemos juntos y finalmente lo intentas tú.',
    icon: 'support'
  },
  {
    title: 'Revisión de errores',
    desc: 'Aprenderás a leer los mensajes de error de la terminal. Equivocarse es parte clave del proceso para programar mejor.',
    icon: 'alert'
  },
  {
    title: 'Refuerzo a tu propio ritmo',
    desc: 'Si necesitas repetir un tema 3 veces, lo repetimos. Aquí no hay presiones, avanzamos según te sientas cómodo.',
    icon: 'chart'
  },
  {
    title: 'Modalidad flexible',
    desc: 'Clases online por Google Meet con pizarra digital interactiva y material digital de apoyo.',
    icon: 'globe'
  }
])
</script>

<template>
  <section class="how-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">Metodología de trabajo</span>
        <h2 class="section-title">¿Cómo es la experiencia de clase?</h2>
        <p class="section-subtitle">
          Un proceso centrado en el alumno, diseñado para fomentar la autonomía y la comprensión profunda de la lógica de programación.
        </p>
      </div>

      <div class="how-grid">
        <div class="how-features-list">
          <div 
            v-for="(feature, index) in features" 
            :key="index" 
            class="feature-card glass-panel"
          >
            <div class="feature-icon-wrapper">
              <svg v-if="feature.icon === 'search'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
              </svg>
              <svg v-else-if="feature.icon === 'map'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 20l-5.447-2.724A1 1 0 013 16.382V5.618a1 1 0 011.447-.894L9 7m0 13l6-3m-6 3V7m6 10l4.553 2.276A1 1 0 0021 18.382V7.618a1 1 0 00-.553-.894L15 4m0 13V4m0 0L9 7" />
              </svg>
              <svg v-else-if="feature.icon === 'document'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
              </svg>
              <svg v-else-if="feature.icon === 'support'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
              </svg>
              <svg v-else-if="feature.icon === 'alert'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
              </svg>
              <svg v-else-if="feature.icon === 'chart'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
              </svg>
              <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9" />
              </svg>
            </div>
            <div class="feature-text">
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.desc }}</p>
            </div>
          </div>
        </div>

        <!-- A sticky summary card to build value and trust -->
        <div class="how-summary-wrapper">
          <div class="summary-card glass-panel">
            <h3 class="summary-title">Resumen del servicio</h3>
            <ul class="summary-list">
              <li>
                <span class="check-icon">✓</span>
                <div>
                  <strong>Clases 100% personalizadas</strong>
                  <p>Adaptadas a tu colegio o universidad.</p>
                </div>
              </li>
              <li>
                <span class="check-icon">✓</span>
                <div>
                  <strong>Apoyo fuera de horario</strong>
                  <p>Resolución de dudas rápidas por WhatsApp.</p>
                </div>
              </li>
              <li>
                <span class="check-icon">✓</span>
                <div>
                  <strong>Práctica continua</strong>
                  <p>Guías y desafíos entre sesiones.</p>
                </div>
              </li>
              <li>
                <span class="check-icon">✓</span>
                <div>
                  <strong>Sin contratos ni amarras</strong>
                  <p>Pagas por clase (individual o bloque de 2 horas).</p>
                </div>
              </li>
            </ul>
            <div class="summary-quote">
              "Mi meta es que no dependas de mí, sino que aprendas a pensar como programador."
              <span>- Juan Erices</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.how-section {
  background-color: var(--bg-secondary);
}

.how-grid {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 40px;
  align-items: start;
}

.how-features-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.feature-card {
  display: flex;
  gap: 20px;
  padding: 24px;
  background-color: var(--bg-primary);
  border: 1px solid var(--border-color);
}

.feature-card:hover {
  transform: translateX(5px);
  border-color: var(--accent);
}

.feature-emoji {
  font-size: 2rem;
  background: var(--bg-tertiary);
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  flex-shrink: 0;
  border: 1px solid var(--border-color);
}

.feature-text h3 {
  font-size: 1.2rem;
  margin-bottom: 6px;
  color: var(--text-primary);
}

.feature-text p {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

/* Summary Card (Right Column) */
.how-summary-wrapper {
  position: sticky;
  top: 110px;
}

.summary-card {
  padding: 30px;
  background: linear-gradient(145deg, var(--bg-secondary) 0%, rgba(var(--accent-rgb), 0.05) 100%);
  border: 1px solid rgba(var(--accent-rgb), 0.15);
}

.summary-title {
  font-size: 1.4rem;
  margin-bottom: 24px;
  border-bottom: 1px solid var(--border-color);
  padding-bottom: 12px;
}

.summary-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 24px;
}

.summary-list li {
  display: flex;
  gap: 12px;
  align-items: flex-start;
}

.check-icon {
  color: var(--accent-green);
  font-weight: 700;
  font-size: 1.2rem;
  background-color: rgba(var(--accent-green-rgb), 0.1);
  width: 24px;
  height: 24px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.summary-list li strong {
  font-size: 0.95rem;
  color: var(--text-primary);
  display: block;
}

.summary-list li p {
  font-size: 0.85rem;
  color: var(--text-secondary);
}

.summary-quote {
  background-color: var(--bg-primary);
  padding: 16px;
  border-radius: 8px;
  border-left: 4px solid var(--accent);
  font-style: italic;
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.4;
}

.summary-quote span {
  display: block;
  margin-top: 8px;
  font-weight: 600;
  color: var(--text-primary);
  font-style: normal;
  font-size: 0.8rem;
}

@media (max-width: 992px) {
  .how-grid {
    grid-template-columns: 1fr;
  }
  .how-summary-wrapper {
    position: static;
  }
}
</style>
