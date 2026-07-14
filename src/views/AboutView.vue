<script setup>
import AboutNav from '../components/about/AboutNav.vue'
import AboutHero from '../components/about/AboutHero.vue'
import AboutSkills from '../components/about/AboutSkills.vue'
import AboutProjects from '../components/about/AboutProjects.vue'
import AboutExperience from '../components/about/AboutExperience.vue'
import AboutRecruiterCta from '../components/about/AboutRecruiterCta.vue'

defineProps({
  whatsappLink: String,
  phoneNumber: String,
  contactEmail: String,
  currentAvailability: String
})
</script>

<template>
  <div class="tech-portfolio-wrapper">
    <!-- Barra de Navegación Exclusiva del Portafolio Técnico -->
    <AboutNav />

    <!-- Contenedor Ejecutivo Principal -->
    <main class="tech-portfolio-container">
      <AboutHero 
        :whatsapp-link="whatsappLink"
        :phone-number="phoneNumber"
        :contact-email="contactEmail"
      />

      <AboutSkills />

      <AboutProjects />

      <AboutExperience />

      <AboutRecruiterCta 
        :phone-number="phoneNumber"
        :contact-email="contactEmail"
      />
    </main>

    <!-- Footer Arquitectónico -->
    <footer class="tech-footer">
      <div class="footer-container">
        <div class="footer-brand">
          <span class="mono-tag">JE //</span> JUAN ERICES FUENTEALBA &middot; SOFTWARE ENGINEER
        </div>
        <div class="footer-note">
          Diseño arquitectónico exclusivo &middot; Built with Vue.js 3 & Tailwind CSS Architecture
        </div>
        <div class="footer-links">
          <router-link to="/" class="return-site-link">← Volver al sitio web de clases particulares</router-link>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Aislamiento visual total respecto a la página de clases de programación */
.tech-portfolio-wrapper {
  background-color: #06080d;
  color: #f1f5f9;
  min-height: 100vh;
  padding-top: 76px;
  font-family: 'Inter', system-ui, -apple-system, sans-serif;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
}

.tech-portfolio-container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 32px;
}

.tech-footer {
  background: #040508;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  padding: 48px 32px;
  margin-top: 40px;
}

.footer-container {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  text-align: center;
}

.footer-brand {
  font-family: monospace;
  font-weight: 800;
  font-size: 0.9rem;
  color: #ffffff;
  letter-spacing: 0.05em;
}

.mono-tag {
  color: #10b981;
}

.footer-note {
  font-size: 0.8rem;
  color: #64748b;
  font-family: monospace;
}

.footer-links {
  margin-top: 16px;
}

.return-site-link {
  font-size: 0.82rem;
  font-weight: 600;
  color: #94a3b8;
  text-decoration: none;
  transition: color 0.25s ease;
  border-bottom: 1px solid transparent;
  padding-bottom: 2px;
}

.return-site-link:hover {
  color: #10b981;
  border-bottom-color: #10b981;
}

@media (max-width: 640px) {
  .tech-portfolio-container {
    padding: 0 20px;
  }
}
</style>
