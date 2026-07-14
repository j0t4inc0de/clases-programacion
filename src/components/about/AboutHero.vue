<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  whatsappLink: String,
  phoneNumber: String,
  contactEmail: String
})

const copiedEmail = ref(false)

const copyEmailToClipboard = () => {
  const email = props.contactEmail || 'jericesb5@gmail.com'
  navigator.clipboard.writeText(email)
  copiedEmail.value = true
  setTimeout(() => {
    copiedEmail.value = false
  }, 3000)
}

const recruiterWhatsappLink = computed(() => {
  const phone = props.phoneNumber || '56948991554'
  const text = encodeURIComponent('Hola Juan, estuve revisando tu portafolio web en /about y me gustaría conversar contigo respecto a una oportunidad laboral.')
  return `https://wa.me/${phone}?text=${text}`
})
</script>

<template>
  <section id="perfil" class="hero-section">
    <!-- Grid arquitectónico sutil de fondo -->
    <div class="bg-grid-overlay"></div>

    <div class="hero-content">
      <div class="status-row">
        <div class="location-tag">
          <svg class="icon-sm" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
            <path stroke-linecap="round" stroke-linejoin="round" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
          </svg>
          <span>Viña del Mar, Valparaíso, Chile (Remoto / Híbrido)</span>
        </div>
      </div>

      <h1 class="hero-title">
        JUAN ERICES <span class="accent-text">FUENTEALBA</span>
      </h1>

      <div class="role-statement">
        <span class="role-bracket">[</span>
        Ingeniero en Informática &middot; Especialista Frontend Vue.js &middot; IoT & Micro-SaaS
        <span class="role-bracket">]</span>
      </div>

      <p class="hero-description">
        Ingeniero en Informática con sólida especialización en desarrollo de interfaces SPA reactivas con <strong>Vue.js 3, Composition API y Tailwind CSS</strong>. Experiencia comprobada construyendo tableros de control en tiempo real para sensores IoT en terreno, sistemas de validación masiva con <strong>Python y Django REST Framework</strong>, y orquestación de infraestructuras de servidores Linux en arquitectura Zero-Trust.
      </p>

      <div class="cta-actions">
        <a :href="recruiterWhatsappLink" target="_blank" rel="noopener noreferrer" class="btn-primary-tech">
          <svg class="btn-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
          </svg>
          <span>Agendar Entrevista</span>
        </a>

        <button @click="copyEmailToClipboard" class="btn-secondary-tech">
          <svg class="btn-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
          </svg>
          <span>{{ copiedEmail ? 'Correo Copiado al Portapapeles' : 'jericesb5@gmail.com' }}</span>
        </button>

        <a href="https://www.linkedin.com/in/juan-erices-fuentealba-628b4a27a/" target="_blank" rel="noopener noreferrer" class="btn-outline-tech" title="LinkedIn">
          <svg class="btn-icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M19 3a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h14m-.5 15.5v-5.3a3.26 3.26 0 0 0-3.26-3.26c-.85 0-1.84.52-2.28 1.3v-1.11h-2.79v8.37h2.79v-4.93c0-.77.62-1.4 1.39-1.4a1.4 1.4 0 0 1 1.4 1.4v4.93h2.75M6.46 10.9v8.37H9.2v-8.37H6.46M7.83 6.67a1.64 1.64 0 0 0-1.64 1.64a1.64 1.64 0 0 0 1.64 1.64 1.64 1.64 0 0 0 1.64-1.64 1.64 1.64 0 0 0-1.64-1.64Z"/>
          </svg>
          <span>LinkedIn</span>
        </a>

        <a href="https://github.com/j0t4inc0de/j0tainc0de" target="_blank" rel="noopener noreferrer" class="btn-outline-tech" title="GitHub">
          <svg class="btn-icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.87 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2Z"/>
          </svg>
          <span>GitHub</span>
        </a>
      </div>

      <div class="tech-metrics-panel">
        <div class="metric-item">
          <span class="metric-value">VUE.JS 3</span>
          <span class="metric-label">Stack Core & Dashboards IoT</span>
        </div>
        <div class="metric-divider"></div>
        <div class="metric-item">
          <span class="metric-value">6+ PROYECTOS</span>
          <span class="metric-label">Producción (SaaS, IoT, Bio-IA)</span>
        </div>
        <div class="metric-divider"></div>
        <div class="metric-item">
          <span class="metric-value">SELLO DAE 2025</span>
          <span class="metric-label">Galardón Innovación Tecnológica</span>
        </div>
        <div class="metric-divider"></div>
        <div class="metric-item">
          <span class="metric-value">LINUX ZERO-TRUST</span>
          <span class="metric-label">DevOps & Orquestación Docker</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  padding: 80px 0 60px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.bg-grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
                    linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
  background-size: 32px 32px;
  pointer-events: none;
  z-index: 0;
}

.hero-content {
  position: relative;
  z-index: 1;
}

.status-row {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 20px;
  margin-bottom: 32px;
}

.status-indicator {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 6px 14px;
  background: rgba(16, 185, 129, 0.1);
  border: 1px solid rgba(16, 185, 129, 0.3);
  border-radius: 4px;
}

.status-dot {
  width: 8px;
  height: 8px;
  background-color: #10b981;
  border-radius: 50%;
  box-shadow: 0 0 8px #10b981;
}

.status-text {
  font-family: monospace;
  font-size: 0.78rem;
  font-weight: 700;
  color: #10b981;
  letter-spacing: 0.06em;
}

.location-tag {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 0.85rem;
  color: #94a3b8;
}

.icon-sm {
  width: 16px;
  height: 16px;
  color: #64748b;
}

.hero-title {
  font-size: 4rem;
  font-weight: 900;
  letter-spacing: -0.04em;
  color: #ffffff;
  line-height: 1.05;
  margin-bottom: 18px;
  font-family: var(--font-heading);
}

.accent-text {
  color: #10b981;
}

.role-statement {
  font-family: monospace;
  font-size: 1.15rem;
  color: #e2e8f0;
  margin-bottom: 28px;
  letter-spacing: 0.02em;
}

.role-bracket {
  color: #10b981;
  font-weight: 700;
  margin: 0 4px;
}

.hero-description {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #94a3b8;
  max-width: 860px;
  margin-bottom: 44px;
}

.hero-description strong {
  color: #ffffff;
  font-weight: 600;
}

/* Botones de acción minimalistas técnicos */
.cta-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  align-items: center;
  margin-bottom: 56px;
}

.btn-icon {
  width: 18px;
  height: 18px;
}

.btn-primary-tech {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  background: #10b981;
  color: #080a0f;
  font-weight: 700;
  font-size: 0.95rem;
  border-radius: 6px;
  text-decoration: none;
  transition: all 0.25s ease;
}

.btn-primary-tech:hover {
  background: #059669;
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(16, 185, 129, 0.3);
}

.btn-secondary-tech {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 24px;
  background: rgba(255, 255, 255, 0.04);
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.15);
  font-weight: 600;
  font-size: 0.92rem;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.25s ease;
}

.btn-secondary-tech:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: #10b981;
}

.btn-outline-tech {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 14px 20px;
  background: transparent;
  color: #94a3b8;
  border: 1px solid rgba(255, 255, 255, 0.1);
  font-weight: 600;
  font-size: 0.9rem;
  border-radius: 6px;
  text-decoration: none;
  transition: all 0.25s ease;
}

.btn-outline-tech:hover {
  color: #ffffff;
  border-color: rgba(255, 255, 255, 0.3);
  background: rgba(255, 255, 255, 0.04);
}

/* Panel de métricas minimalista */
.tech-metrics-panel {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr auto 1fr;
  align-items: center;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 8px;
  padding: 24px 32px;
}

.metric-item {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.metric-value {
  font-family: monospace;
  font-size: 1.25rem;
  font-weight: 800;
  color: #ffffff;
  letter-spacing: 0.02em;
}

.metric-label {
  font-size: 0.8rem;
  color: #64748b;
  font-weight: 500;
}

.metric-divider {
  width: 1px;
  height: 40px;
  background: rgba(255, 255, 255, 0.08);
  margin: 0 20px;
}

@media (max-width: 1024px) {
  .hero-title {
    font-size: 3.2rem;
  }
  .tech-metrics-panel {
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }
  .metric-divider {
    display: none;
  }
}

@media (max-width: 640px) {
  .hero-section {
    padding: 105px 0 60px;
  }
  .meta-bar {
    flex-direction: column;
    align-items: flex-start;
    gap: 12px;
  }
  .hero-title {
    font-size: 2.15rem;
    line-height: 1.15;
    margin-bottom: 14px;
  }
  .role-statement {
    font-size: 0.98rem;
    margin-bottom: 22px;
  }
  .hero-description {
    font-size: 0.95rem;
    line-height: 1.65;
    margin-bottom: 34px;
  }
  .cta-actions {
    flex-direction: column;
    align-items: stretch;
    gap: 12px;
    margin-bottom: 40px;
  }
  .btn-primary-tech,
  .btn-secondary-tech,
  .btn-outline-tech {
    justify-content: center;
    width: 100%;
    padding: 13px 20px;
  }
  .tech-metrics-panel {
    grid-template-columns: 1fr;
    gap: 18px;
    padding: 18px 20px;
  }
}

@media (max-width: 400px) {
  .hero-title {
    font-size: 1.85rem;
  }
}
</style>
