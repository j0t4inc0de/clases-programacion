<script setup>
import { computed } from 'vue'

const props = defineProps({
  phoneNumber: String,
  contactEmail: String
})

const recruiterWhatsappLink = computed(() => {
  const phone = props.phoneNumber || '56948991554'
  const text = encodeURIComponent('Hola Juan, he revisado tu portafolio en /about y nos gustaría coordinar una conversación técnica para conocer tu perfil.')
  return `https://wa.me/${phone}?text=${text}`
})
</script>

<template>
  <section id="contacto" class="recruiter-cta-section">
    <div class="cta-box">
      <div class="cta-header-mono">
        <span class="section-number">05 / CONTACTO & CONTRATACIÓN</span>
        <h3 class="cta-main-title">¿POR QUÉ INTEGRAR A JUAN ERICES A TU EQUIPO?</h3>
        <p class="cta-subtitle">
          Tres pilares diferenciales de un ingeniero que combina interfaces frontend modernas con la solidez arquitectónica de backend e infraestructura Linux.
        </p>
      </div>

      <div class="reasons-grid">
        <div class="reason-card">
          <div class="reason-num">01 // FRONTEND CORE & IOT</div>
          <h4>Especialista en Interfaces Reactivas</h4>
          <p>
            Dominio de <strong>Vue.js 3, Composition API, Pinia y Tailwind CSS</strong>. Experiencia verificable en tableros de alta densidad, tablas de alto volumen, exportaciones nativas y seguridad por roles (RBAC).
          </p>
        </div>

        <div class="reason-card">
          <div class="reason-num">02 // FULL-STACK & PYTHON</div>
          <h4>Visión 360° & Cero Cajas Negras</h4>
          <p>
            Capacidad para diseñar APIs sólidas con <strong>Django REST Framework, FastAPI y PostgreSQL</strong> e integrar motores de inteligencia artificial con biometría facial, logrando una comunicación técnica fluida con todas las áreas del equipo.
          </p>
        </div>

        <div class="reason-card">
          <div class="reason-num">03 // DEVOPS & ZERO-TRUST</div>
          <h4>Autonomía en Infraestructura Linux</h4>
          <p>
            Mentalidad resolutiva y proactiva en el despliegue de servidores <strong>Ubuntu 24.04 LTS</strong> orquestando +24 microservicios en Docker Compose con protección <strong>Cloudflare Tunnels y Tailscale Mesh VPN</strong>.
          </p>
        </div>
      </div>

      <div class="contact-card">
        <div class="contact-info">
          <h4>DISPONIBLE PARA PROCESOS DE SELECCIÓN</h4>
          <p>Modalidad Remota, Híbrida o Presencial según requerimientos del proyecto.</p>
        </div>
        
        <div class="contact-actions">
          <a :href="recruiterWhatsappLink" target="_blank" rel="noopener noreferrer" class="btn-cta-whatsapp">
            <svg class="btn-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
            </svg>
            <span>Contactar vía WhatsApp</span>
          </a>

          <a :href="`mailto:${contactEmail || 'jericesb5@gmail.com'}?subject=Oportunidad%20Laboral%20-%20Portafolio%20Juan%20Erices`" class="btn-cta-email">
            <svg class="btn-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
            <span>Enviar Correo Electrónico</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.recruiter-cta-section {
  padding: 80px 0 100px 0;
}

.cta-box {
  background: rgba(255, 255, 255, 0.015);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 8px;
  padding: 56px 48px;
}

.cta-header-mono {
  margin-bottom: 48px;
  max-width: 800px;
}

.section-number {
  font-family: monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #10b981;
  letter-spacing: 0.1em;
  display: block;
  margin-bottom: 12px;
}

.cta-main-title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 14px;
  letter-spacing: -0.02em;
}

.cta-subtitle {
  font-size: 1.05rem;
  color: #94a3b8;
  line-height: 1.7;
}

.reasons-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-bottom: 48px;
}

.reason-card {
  padding: 28px;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 6px;
  transition: all 0.25s ease;
}

.reason-card:hover {
  border-color: rgba(16, 185, 129, 0.4);
  background: rgba(16, 185, 129, 0.03);
}

.reason-num {
  font-family: monospace;
  font-size: 0.78rem;
  font-weight: 700;
  color: #10b981;
  margin-bottom: 14px;
  letter-spacing: 0.06em;
}

.reason-card h4 {
  font-size: 1.2rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 12px;
}

.reason-card p {
  font-size: 0.92rem;
  line-height: 1.65;
  color: #94a3b8;
}

.reason-card p strong {
  color: #ffffff;
}

/* Contact Card Final */
.contact-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 32px;
  padding: 32px 36px;
  background: #080a0f;
  border: 1px solid rgba(16, 185, 129, 0.3);
  border-radius: 6px;
}

.contact-info h4 {
  font-family: monospace;
  font-size: 1.15rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 6px;
  letter-spacing: 0.04em;
}

.contact-info p {
  font-size: 0.92rem;
  color: #94a3b8;
}

.contact-actions {
  display: flex;
  gap: 16px;
  flex-shrink: 0;
}

.btn-icon {
  width: 18px;
  height: 18px;
}

.btn-cta-whatsapp {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 24px;
  background: #10b981;
  color: #080a0f;
  font-weight: 700;
  font-size: 0.92rem;
  border-radius: 4px;
  text-decoration: none;
  transition: all 0.25s ease;
}

.btn-cta-whatsapp:hover {
  background: #059669;
  transform: translateY(-2px);
}

.btn-cta-email {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 24px;
  background: rgba(255, 255, 255, 0.04);
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.15);
  font-weight: 600;
  font-size: 0.92rem;
  border-radius: 4px;
  text-decoration: none;
  transition: all 0.25s ease;
}

.btn-cta-email:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: #10b981;
}

@media (max-width: 992px) {
  .reasons-grid {
    grid-template-columns: 1fr;
  }
  .contact-card {
    flex-direction: column;
    text-align: center;
  }
  .contact-actions {
    flex-direction: column;
    width: 100%;
  }
  .contact-actions a {
    justify-content: center;
  }
}

@media (max-width: 640px) {
  .cta-box {
    padding: 36px 20px;
  }
  .cta-main-title {
    font-size: 1.8rem;
  }
}
</style>
