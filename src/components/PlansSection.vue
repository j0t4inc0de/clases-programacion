<script setup>
import { ref } from 'vue'

const props = defineProps({
  phoneNumber: {
    type: String,
    required: true
  }
})

const getWhatsappLink = (message) => {
  return `https://wa.me/${props.phoneNumber}?text=${encodeURIComponent(message)}`
}

const plans = ref([
  {
    name: 'Clase Individual',
    subtitle: 'Ideal para resolver dudas específicas',
    price: '$16.000 CLP',
    period: 'por 1 hora',
    desc: 'Sesión de 60 minutos ideal para resolver problemas de código, guías de ejercicios específicas o desatascarte en un bug puntual.',
    features: [
      'Clase online 1-a-1 por Google Meet',
      'Pizarra digital y código compartido',
      'Resolución de dudas específicas',
      'Acceso al material visto en clases',
      'Grabación opcional de la sesión'
    ],
    popular: false,
    cta: 'Agendar Clase',
    message: '¡Hola Juan! Me gustaría agendar una Clase Individual de 1 hora para resolver dudas de programación.'
  },
  {
    name: 'Bloque de 2 Horas',
    subtitle: 'Recomendado para repasar o certámenes',
    price: '$25.000 CLP',
    period: 'por 2 horas',
    desc: 'Sesión intensiva enfocada al 100% en resolver una tarea, certamen o avanzar materia más rápido con apoyo continuo.',
    features: [
      'Clase online por Google Meet',
      'Ahorra $7.000 CLP en total',
      'Resolución de guías y pruebas reales',
      'Prioridad de agendamiento rápido',
      'Apoyo rápido vía chat post-clase'
    ],
    popular: true,
    cta: 'Agendar Bloque',
    isTwoHours: true,
    message: '¡Hola Juan! Me gustaría agendar un Bloque de 2 Horas para repasar materia o preparar evaluaciones.'
  },
  {
    name: 'Clase Diagnóstica',
    subtitle: 'Auditoría inicial de tu nivel',
    price: 'Gratis',
    period: 'primera sesión',
    desc: 'Reunión de 20-30 minutos por Google Meet para evaluar tus conocimientos, revisar tus guías de estudio, y trazar una ruta personalizada sin costo.',
    features: [
      'Reunión 1-a-1 por Google Meet',
      'Diagnóstico de tu nivel técnico actual',
      'Revisión y desglose de tu programa de estudio',
      'Planificación de la mejor estrategia de aprendizaje',
      'Totalmente gratuito y sin compromisos'
    ],
    popular: false,
    cta: 'Agendar Clase',
    message: '¡Hola Juan! Me gustaría agendar la Clase Diagnóstica Gratis para evaluar mi nivel inicial y conversar sobre las clases.'
  }
])
</script>

<template>
  <section id="planes" class="plans-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">Valor de Clases & Ritmo</span>
        <h2 class="section-title">Tarifas transparentes y avance a tu propio ritmo</h2>
        <p class="section-subtitle">
          Sin planes rígidos ni contratos mensuales. Cada clase continúa exactamente donde quedó la anterior, adaptándome al ritmo de aprendizaje del estudiante.
        </p>
      </div>

      <div class="plans-grid">
        <div 
          v-for="(plan, index) in plans" 
          :key="index" 
          class="plan-card glass-panel"
          :class="{ 'popular-card': plan.popular }"
        >
          <div v-if="plan.popular" class="popular-badge">Recomendado</div>
          
          <div class="plan-header">
            <h3 class="plan-name">{{ plan.name }}</h3>
            <p class="plan-subtitle">{{ plan.subtitle }}</p>
          </div>
          
          <div class="plan-price-section">
            <span class="plan-price">{{ plan.price }}</span>
            <span class="plan-period">{{ plan.period }}</span>
          </div>

          <p class="plan-description">{{ plan.desc }}</p>

          <ul class="plan-features">
            <li v-for="(feat, fIdx) in plan.features" :key="fIdx">
              <span class="feat-check">✓</span>
              <span>{{ feat }}</span>
            </li>
          </ul>

          <a 
            v-if="plan.isTwoHours"
            :href="getWhatsappLink(plan.message)" 
            target="_blank" 
            rel="noopener noreferrer"
            class="btn-accent-anim plan-cta"
          >
            <div class="circle c-1"></div>
            <div class="circle c-2"></div>
            <div class="circle c-3"></div>
            <div class="circle c-4"></div>
            <span class="btn-text">{{ plan.cta }}</span>
          </a>
          <a 
            v-else
            :href="getWhatsappLink(plan.message)" 
            target="_blank" 
            rel="noopener noreferrer"
            class="btn plan-cta"
            :class="plan.popular ? 'btn-whatsapp pulse-btn' : 'btn-secondary'"
          >
            {{ plan.cta }}
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.plans-section {
  background-color: var(--bg-primary);
}

.plans-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 30px;
  align-items: stretch;
}

.plan-card {
  padding: 40px 30px;
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  display: flex;
  flex-direction: column;
  position: relative;
  height: 100%;
}

.plan-card:hover {
  transform: translateY(-5px);
}

/* Featured / Popular styling */
.popular-card {
  border: 2px solid var(--accent);
  box-shadow: 0 25px 50px -12px rgba(var(--accent-rgb), 0.15);
}

.popular-badge {
  position: absolute;
  top: -15px;
  left: 50%;
  transform: translateX(-50%);
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-green) 100%);
  color: #ffffff;
  padding: 6px 18px;
  border-radius: 50px;
  font-family: var(--font-heading);
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  box-shadow: 0 4px 10px rgba(var(--accent-rgb), 0.3);
}

.plan-header {
  margin-bottom: 24px;
  border-bottom: 1px solid var(--border-color);
  padding-bottom: 20px;
}

.plan-name {
  font-size: 1.4rem;
  margin-bottom: 6px;
  color: var(--text-primary);
}

.plan-subtitle {
  font-size: 0.9rem;
  color: var(--accent);
  font-weight: 600;
}

.popular-card .plan-subtitle {
  color: var(--accent-green);
}

.plan-price-section {
  margin-bottom: 24px;
  display: flex;
  align-items: baseline;
  gap: 8px;
}

.plan-price {
  font-family: var(--font-heading);
  font-size: 2rem;
  font-weight: 800;
  color: var(--accent);
}

.popular-card .plan-price {
  color: var(--accent-green);
}

.plan-period {
  font-size: 0.85rem;
  color: var(--text-secondary);
}

.plan-description {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.5;
  margin-bottom: 28px;
}

.plan-features {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 36px;
  flex-grow: 1;
}

.plan-features li {
  display: flex;
  gap: 10px;
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.4;
  align-items: flex-start;
}

.feat-check {
  color: var(--accent-green);
  font-weight: bold;
}

.plan-cta {
  width: 100%;
}

@media (max-width: 576px) {
  .plan-card {
    padding: 30px 20px;
  }
}
</style>
