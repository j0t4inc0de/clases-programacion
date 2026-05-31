<script setup>
import { ref } from 'vue'

defineProps({
  whatsappLink: {
    type: String,
    required: true
  },
  email: {
    type: String,
    default: 'jericesb5@gmail.com'
  },
  availability: {
    type: String,
    default: 'Lunes a Viernes: 15:00 - 21:00 | Sábados: 10:00 - 17:00'
  }
})

const copied = ref(false)

const copyEmail = (emailStr) => {
  navigator.clipboard.writeText(emailStr)
  copied.value = true
  setTimeout(() => {
    copied.value = false
  }, 2000)
}
</script>

<template>
  <section id="contacto" class="contact-section">
    <div class="glow-orb contact-orb"></div>
    
    <div class="container contact-container">
      <div class="contact-card glass-panel">
        <span class="contact-tag-badge">
          <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" style="display:inline-block; vertical-align:middle; margin-right:6px; margin-top:-2px;">
            <path d="M13 2L3 14h9v8l10-12h-9l1z"/>
          </svg>
          Empecemos ya
        </span>
        <h2 class="contact-title">¿Listo para mejorar tus notas y entender el código?</h2>
        <p class="contact-cta-text">
          Agenda tu primera clase y empecemos a reforzar programación paso a paso.
        </p>

        <div class="contact-methods-grid">
          <!-- WhatsApp Card -->
          <div class="method-card whatsapp-method">
            <div class="method-icon-wrapper">
              <svg class="method-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" fill="currentColor">
                <path d="M380.9 97.1C339 55.1 283.2 32 223.9 32c-122.4 0-222 99.6-222 222 0 39.1 10.2 77.3 29.6 111L3 480l117.7-30.9c32.4 17.7 68.9 27 106.1 27h.1c122.3 0 224.1-99.6 224.1-222 0-59.3-25.2-115-67.1-157zm-157 341.6c-33.2 0-65.7-8.9-94-25.7l-6.7-4-69.8 18.3L72 359.2l-4.4-7c-18.5-29.4-28.2-63.3-28.2-98.2 0-101.7 82.8-184.5 184.6-184.5 49.3 0 95.6 19.2 130.4 54.1 34.8 34.9 56.2 81.2 56.1 130.5 0 101.8-84.9 184.6-186.6 184.6zm101.2-138.2c-5.5-2.8-32.8-16.2-37.9-18-5.1-1.9-8.8-2.8-12.5 2.8-3.7 5.6-14.3 18-17.6 21.8-3.2 3.7-6.5 4.2-12 1.4-32.6-16.3-54-29.1-75.5-66-5.7-9.8 5.7-9.1 16.3-30.3 1.8-3.7.9-6.9-.5-9.7-1.4-2.8-12.5-30.1-17.1-41.2-4.5-10.8-9.1-9.3-12.5-9.5-3.2-.2-6.9-.2-10.6-.2-3.7 0-9.7 1.4-14.8 6.9-5.1 5.6-19.4 19-19.4 46.3 0 27.3 19.9 53.7 22.6 57.4 2.8 3.7 39.1 59.7 94.8 83.8 35.2 15.2 49 16.5 66.6 13.9 10.7-1.6 32.8-13.4 37.4-26.4 4.6-13 4.6-24.1 3.2-26.4-1.3-2.5-5-3.9-10.5-6.6z"/>
              </svg>
            </div>
            <h3>WhatsApp</h3>
            <p>Respuesta rápida y directa para agendar tu horario.</p>
            <a :href="whatsappLink" target="_blank" rel="noopener noreferrer" class="btn btn-whatsapp pulse-btn method-btn">
              Quiero agendar una clase
            </a>
          </div>

          <!-- Info Details Card -->
          <div class="method-card info-method">
            <div class="info-block">
              <span class="info-label">
                <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="display:inline-block; vertical-align:middle; margin-right:6px; margin-top:-2px;">
                  <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                  <polyline points="22,6 12,13 2,6"/>
                </svg>
                Correo Electrónico
              </span>
              <div class="email-copy-wrapper">
                <span class="email-text">{{ email }}</span>
                <button @click="copyEmail(email)" class="copy-btn" :class="{ 'copied': copied }">
                  {{ copied ? '¡Copiado!' : 'Copiar' }}
                </button>
              </div>
            </div>

            <div class="info-block">
              <span class="info-label">
                <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="display:inline-block; vertical-align:middle; margin-right:6px; margin-top:-2px;">
                  <circle cx="12" cy="12" r="10"/>
                  <polyline points="12 6 12 12 16 14"/>
                </svg>
                Disponibilidad Horaria
              </span>
              <p class="availability-text">{{ availability }}</p>
              <span class="availability-notice">*Zona horaria: Santiago de Chile (GMT-4)*</span>
            </div>
          </div>
        </div>

        <div class="contact-footer">
          <p>© 2026 Juan Erices. Clases particulares de programación.</p>
          <p>Hecho con dedicación para estudiantes de educación media y superior.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  background-color: var(--bg-primary);
  padding: 100px 0 50px 0;
  overflow: hidden;
}

.contact-container {
  display: flex;
  justify-content: center;
}

.contact-card {
  width: 100%;
  max-width: 900px;
  padding: 60px;
  text-align: center;
  background: linear-gradient(135deg, var(--bg-secondary) 0%, rgba(var(--accent-rgb), 0.03) 100%);
  border: 1px solid rgba(var(--accent-rgb), 0.1);
  box-shadow: 0 30px 60px -20px rgba(0, 0, 0, 0.4);
}

.contact-tag-badge {
  display: inline-block;
  background-color: rgba(var(--accent-green-rgb), 0.1);
  color: var(--accent-green);
  font-family: var(--font-heading);
  font-size: 0.85rem;
  font-weight: 700;
  text-transform: uppercase;
  padding: 6px 16px;
  border-radius: 50px;
  margin-bottom: 24px;
  border: 1px solid rgba(var(--accent-green-rgb), 0.15);
}

.contact-title {
  font-size: 2.2rem;
  line-height: 1.25;
  margin-bottom: 16px;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.contact-cta-text {
  font-size: 1.15rem;
  color: var(--text-secondary);
  margin-bottom: 48px;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.contact-methods-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px;
  margin-bottom: 48px;
  text-align: left;
}

.method-card {
  background-color: rgba(0, 0, 0, 0.15);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  padding: 30px;
  display: flex;
  flex-direction: column;
}

.whatsapp-method {
  border-color: rgba(37, 211, 102, 0.2);
  align-items: center;
  text-align: center;
}

.whatsapp-method h3 {
  font-size: 1.3rem;
  margin-bottom: 10px;
  color: var(--text-primary);
}

.whatsapp-method p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  margin-bottom: 24px;
  max-width: 250px;
}

.method-icon-wrapper {
  background-color: rgba(37, 211, 102, 0.1);
  color: #25d366;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 16px;
}

.method-icon {
  width: 24px;
  height: 24px;
}

.method-btn {
  width: 100%;
}

.info-method {
  gap: 24px;
  justify-content: center;
}

.info-block {
  display: flex;
  flex-direction: column;
}

.info-label {
  font-family: var(--font-heading);
  font-weight: 700;
  font-size: 0.85rem;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 8px;
  letter-spacing: 0.05em;
}

.email-copy-wrapper {
  display: flex;
  background-color: var(--bg-primary);
  border: 1px solid var(--border-color);
  border-radius: 8px;
  padding: 6px 12px;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
}

.email-text {
  font-family: monospace;
  font-size: 0.85rem;
  color: var(--text-primary);
  user-select: all;
  overflow-x: auto;
  white-space: nowrap;
  scrollbar-width: none; /* hide scrollbar for space */
}

.email-text::-webkit-scrollbar {
  display: none;
}

.copy-btn {
  background-color: var(--bg-tertiary);
  color: var(--text-primary);
  border: 1px solid var(--border-color);
  border-radius: 6px;
  padding: 6px 12px;
  font-size: 0.75rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
  white-space: nowrap;
}

.copy-btn:hover {
  background-color: var(--border-color);
  color: var(--accent);
}

.copy-btn.copied {
  background-color: var(--accent-green);
  color: #ffffff;
  border-color: var(--accent-green);
}

.availability-text {
  font-size: 0.95rem;
  color: var(--text-primary);
  font-weight: 500;
  line-height: 1.4;
}

.availability-notice {
  font-size: 0.75rem;
  color: var(--text-secondary);
  margin-top: 4px;
  font-style: italic;
}

.contact-footer {
  border-top: 1px solid var(--border-color);
  padding-top: 24px;
  font-size: 0.8rem;
  color: var(--text-secondary);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

/* Contact glow orb */
.contact-orb {
  bottom: -100px;
  left: 50%;
  transform: translateX(-50%);
  width: 400px;
  height: 400px;
  background-color: rgba(var(--accent-rgb), 0.05);
  filter: blur(120px);
}

@media (max-width: 768px) {
  .contact-card {
    padding: 40px 20px;
  }
  .contact-title {
    font-size: 1.8rem;
  }
  .contact-methods-grid {
    grid-template-columns: 1fr;
  }
}
</style>
