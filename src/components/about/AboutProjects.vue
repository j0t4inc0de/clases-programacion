<script setup>
import { ref, computed } from 'vue'

const selectedCategory = ref('all')

const categories = [
  { id: 'all', name: 'TODOS LOS PROYECTOS' },
  { id: 'iot', name: 'IOT & DASHBOARDS INDUSTRIALES' },
  { id: 'saas', name: 'CLOUD, LINUX & MICRO-SAAS' },
  { id: 'ai', name: 'IA, BIOMETRÍA & SISTEMAS' },
]

const projects = [
  {
    id: 'telemetrics',
    code: ' 01',
    title: 'Telemetrics — Dashboard IoT en Tiempo Real',
    role: 'Ingeniero de Software Frontend',
    company: 'Soluciones Tecnológicas Netzona Spa',
    period: 'May. 2026 - Actualidad',
    category: 'iot',
    summary: 'Dashboard IoT para monitoreo en tiempo real de datos críticos de sensores en terreno con seguridad y control de acceso por roles (RBAC).',
    tags: ['Vue.js 3', 'IoT Architecture', 'Real-Time Data', 'REST APIs', 'RBAC Security', 'Tailwind CSS'],
    liveUrl: 'https://telemetrics.netzona.cl/login',
    githubUrl: null,
    privateNote: null,
    status: 'EN PRODUCCIÓN / INTERNO'
  },
  {
    id: 'efibox',
    code: ' 02',
    title: 'EFIBOX Industrial Dashboard',
    role: 'Ingeniero en Informática — Encargado Frontend',
    company: 'Efintel Ltda.',
    period: 'Jul. 2025 - Mar. 2026',
    category: 'iot',
    summary: 'SPA industrial para control y supervisión operacional de dispositivos IoT, con optimización de tablas masivas y exportación nativa a PDF/Excel.',
    tags: ['Vue.js 3', 'Composition API', 'JavaScript ES6+', 'APIs REST', 'Data Visualization', 'Export PDF/Excel'],
    liveUrl: null,
    githubUrl: null,
    privateNote: 'Información empresarial privada',
    status: 'PLATAFORMA INDUSTRIAL'
  },
  {
    id: 'linux-cloud',
    code: ' 03',
    title: 'Cloud Privada & Microservicios (Linux Server Zero-Trust)',
    role: 'DevOps & Arquitecto de Infraestructura',
    company: 'Infraestructura Propia 24/7',
    period: 'Abr. 2026 - Actualidad',
    category: 'saas',
    summary: 'Servidor Ubuntu 24.04 LTS con orquestación de +24 servicios en Docker Compose, seguridad Zero-Trust (Cloudflare Tunnels) y red Tailscale VPN.',
    tags: ['DevOps', 'Ubuntu 24.04 LTS', 'Docker Compose', 'Cloudflare Tunnels', 'Tailscale VPN', 'PostgreSQL', 'Redis'],
    liveUrl: null,
    githubUrl: null,
    privateNote: 'Informacion privada',
    status: 'INFRAESTRUCTURA ACTIVA'
  },
  {
    id: 'cleanmail',
    code: ' 04',
    title: 'CleanMail — Micro-SaaS de Verificación Masiva de Emails',
    role: 'Full-Stack Engineer & SecOps',
    company: 'SaaS Propio con Pasarela de Pagos',
    period: 'Jun. 2026',
    category: 'saas',
    summary: 'Micro-SaaS de alta velocidad con Django 5, PostgreSQL y workers asíncronos en Redis para validar listas masivas de emails (RFC 5322/DNS MX).',
    tags: ['Vue.js 3', 'Pinia', 'Django 5 REST', 'Redis Workers', 'PostgreSQL', 'Magic Links JWT', 'n8n Webhooks'],
    liveUrl: null,
    githubUrl: 'https://github.com/j0t4inc0de/mailsanitizer',
    privateNote: null,
    status: 'MICRO-SAAS'
  },
  {
    id: 'smartlend',
    code: ' 05',
    title: 'SmartLend — Tótem con Biometría Facial e IA (INACAP)',
    role: 'Desarrollador Full-Stack & AI Integration',
    company: 'INACAP Sede Los Ángeles',
    period: 'Ago. 2023 - Jul. 2026',
    category: 'ai',
    summary: 'Tótem de laboratorio con reconocimiento facial biométrico en milisegundos mediante Python y embeddings vectoriales sobre frontend reactivo Vue 3 + Pinia.',
    tags: ['Python IA / Biometría', 'Vue.js 3', 'Pinia', 'Django REST Framework', 'Embeddings', 'Tótem Táctil'],
    liveUrl: null,
    githubUrl: 'https://github.com/j0t4inc0de/smartlend',
    privateNote: null,
    status: 'PROYECTO ACADÉMICO'
  },
  {
    id: 'wearesamod',
    code: ' 06',
    title: 'We Are Samod — Plataforma Cloud & SaaS Ecosystem',
    role: 'Lead Frontend Developer',
    company: 'We Are Samod',
    period: 'Abr. 2026 - Actualidad',
    category: 'saas',
    summary: 'Desarrollo de frontend SPA de alta velocidad en Vue 3 y Tailwind CSS para automatización inteligente y ciberseguridad cloud.',
    tags: ['Vue 3', 'Tailwind CSS', 'SPA Architecture', 'Micro-animaciones', 'Performance'],
    liveUrl: 'https://wearesamod.com',
    githubUrl: null,
    privateNote: null,
    status: 'EN PRODUCCIÓN'
  },
  {
    id: 'asesorats',
    code: ' 07',
    title: 'Asesora TS — CRM & Sistema de Gestión Empresarial',
    role: 'Python/Django Backend & Full-Stack Developer',
    company: 'Asesora TS',
    period: 'Mar. 2026 - Abr. 2026',
    category: 'saas',
    summary: 'CRM para gestión de expedientes empresariales con modelado relacional sobre Django ORM y control de acceso granular bajo arquitectura MVC/MVT.',
    tags: ['Python', 'Django ORM', 'PostgreSQL', 'RBAC Security', 'MVC/MVT Architecture'],
    liveUrl: 'https://asesora-moyano.wearesamod.com/',
    githubUrl: null,
    privateNote: null,
    status: 'EN PRODUCCIÓN'
  },
  {
    id: 'desafiatp',
    code: ' 08',
    title: 'Olimpiadas Tecnológicas DesafíaT-TP 2025',
    role: 'Desarrollador Web & Coordinador Técnico-Educativo',
    company: 'Liceo Bicentenario Tecnológico El Huertón',
    period: 'Mar. 2025 - Jul. 2025',
    category: 'ai',
    summary: 'Plataforma provincial de olimpiadas tecnológicas (15 liceos) integrada con Moodle y chatbot de asistencia técnica en vivo vía OpenAI.',
    tags: ['WordPress UX/UI', 'Moodle Integration', 'OpenAI Chatbot', 'HTML/CSS/JS', 'EdTech'],
    liveUrl: null,
    githubUrl: null,
    privateNote: 'Informacion empresarial privada',
    status: 'EVENTO COMPLETADO'
  },
  {
    id: 'hogar4patas',
    code: ' 09',
    title: 'Hogar de 4 Patas — Plataforma de Rescate Animal',
    role: 'Full-Stack Developer',
    company: 'Asociado con INACAP',
    period: 'Oct. 2023',
    category: 'ai',
    summary: 'Plataforma web y móvil en Django y Python con alertas geolocalizadas en tiempo real para el rescate y gestión ciudadana de animales.',
    tags: ['Django', 'Python 3', 'JavaScript', 'HTML5 & CSS3', 'Social Impact'],
    liveUrl: null,
    githubUrl: 'https://github.com/j0t4inc0de/hogardepatas',
    privateNote: null,
    status: 'REPOSITORIO ABIERTO'
  }
]

const filteredProjects = computed(() => {
  if (selectedCategory.value === 'all') return projects
  return projects.filter(p => p.category === selectedCategory.value)
})
</script>

<template>
  <section id="proyectos" class="projects-section">
    <div class="section-header-mono">
      <span class="section-number">03 / CASE STUDIES</span>
      <h3 class="section-title">PROYECTOS DE ALTO IMPACTO</h3>
      <p class="section-subtitle">
        Análisis técnico de plataformas en producción: soluciones concisas enfocadas en arquitectura, rendimiento e ingeniería escalable.
      </p>
    </div>

    <!-- Filtro -->
    <div class="projects-filter">
      <button
        v-for="cat in categories"
        :key="cat.id"
        @click="selectedCategory = cat.id"
        class="filter-btn"
        :class="{ active: selectedCategory === cat.id }"
      >
        {{ cat.name }}
      </button>
    </div>

    <!-- Grid de Proyectos 100% Uniforme -->
    <div class="projects-grid">
      <div
        v-for="proj in filteredProjects"
        :key="proj.id"
        class="project-card"
      >
        <div class="project-top">
          <div class="project-meta-left">
            <span class="project-code">{{ proj.code }}</span>
            <span class="project-company">{{ proj.company }}</span>
          </div>
          <span class="project-status">{{ proj.status }}</span>
        </div>

        <h4 class="project-title">{{ proj.title }}</h4>
        <div class="project-role">{{ proj.role }} &middot; {{ proj.period }}</div>

        <p class="project-summary">{{ proj.summary }}</p>

        <!-- Tags -->
        <div class="project-tags">
          <span v-for="tag in proj.tags" :key="tag" class="tech-tag">
            {{ tag }}
          </span>
        </div>

        <!-- Enlaces / Información de Privacidad -->
        <div class="project-actions" v-if="proj.liveUrl || proj.githubUrl || proj.privateNote">
          <a v-if="proj.liveUrl" :href="proj.liveUrl" target="_blank" rel="noopener noreferrer" class="action-btn live-btn">
            <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
            </svg>
            <span>Sitio web oficial</span>
          </a>
          <a v-if="proj.githubUrl" :href="proj.githubUrl" target="_blank" rel="noopener noreferrer" class="action-btn github-btn">
            <svg class="icon-svg" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.87 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2Z"/>
            </svg>
            <span>Ver Repositorio GitHub</span>
          </a>
          <div v-if="proj.privateNote" class="action-btn private-badge-btn" title="Información confidencial o bajo acuerdo de privacidad">
            <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
            </svg>
            <span>{{ proj.privateNote }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: 70px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.section-header-mono {
  margin-bottom: 36px;
  max-width: 760px;
}

.section-number {
  font-family: monospace;
  font-size: 0.82rem;
  font-weight: 700;
  color: #10b981;
  letter-spacing: 0.1em;
  display: block;
  margin-bottom: 10px;
}

.section-title {
  font-size: 2rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 12px;
  letter-spacing: -0.02em;
}

.section-subtitle {
  font-size: 0.98rem;
  color: #94a3b8;
  line-height: 1.6;
}

.projects-filter {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 34px;
}

.filter-btn {
  padding: 7px 16px;
  background: rgba(255, 255, 255, 0.02);
  color: #64748b;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 4px;
  font-family: monospace;
  font-size: 0.75rem;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.25s ease;
  letter-spacing: 0.04em;
}

.filter-btn:hover {
  background: rgba(255, 255, 255, 0.06);
  color: #ffffff;
}

.filter-btn.active {
  background: #10b981;
  color: #080a0f;
  border-color: #10b981;
}

/* Projects Grid - 100% Uniforme & Súper Compacto */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 20px;
}

.project-card {
  display: flex;
  flex-direction: column;
  padding: 24px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.015);
  border: 1px solid rgba(255, 255, 255, 0.07);
  transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
  position: relative;
}

.project-card:hover {
  transform: translateY(-3px);
  border-color: rgba(16, 185, 129, 0.4);
  box-shadow: 0 16px 32px -12px rgba(0, 0, 0, 0.6);
}

.project-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 10px;
}

.project-meta-left {
  display: flex;
  align-items: center;
  gap: 8px;
}

.project-code {
  font-family: monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #10b981;
  padding: 2px 6px;
  background: rgba(16, 185, 129, 0.1);
  border-radius: 3px;
}

.project-company {
  font-size: 0.78rem;
  font-weight: 700;
  color: #e2e8f0;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.project-status {
  font-family: monospace;
  font-size: 0.68rem;
  font-weight: 700;
  color: #64748b;
  padding: 2px 6px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 3px;
}

.project-title {
  font-size: 1.18rem;
  font-weight: 800;
  color: #ffffff;
  line-height: 1.35;
  margin-bottom: 4px;
}

.project-role {
  font-size: 0.8rem;
  color: #94a3b8;
  font-weight: 600;
  margin-bottom: 14px;
}

.project-summary {
  font-size: 0.88rem;
  line-height: 1.6;
  color: #cbd5e1;
  margin-bottom: 18px;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 18px;
  margin-top: auto;
}

.tech-tag {
  font-family: monospace;
  font-size: 0.72rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 3px;
  background: rgba(255, 255, 255, 0.04);
  color: #94a3b8;
  border: 1px solid rgba(255, 255, 255, 0.06);
}

.project-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  padding-top: 14px;
  border-top: 1px solid rgba(255, 255, 255, 0.06);
}

.action-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 0.8rem;
  font-weight: 600;
  padding: 7px 12px;
  border-radius: 4px;
  text-decoration: none;
  transition: all 0.25s ease;
}

.github-btn {
  background: rgba(255, 255, 255, 0.04);
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.github-btn:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: #10b981;
  color: #10b981;
}

.live-btn {
  background: rgba(16, 185, 129, 0.1);
  color: #10b981;
  border: 1px solid rgba(16, 185, 129, 0.3);
}

.live-btn:hover {
  background: rgba(16, 185, 129, 0.2);
}

.private-badge-btn {
  background: rgba(255, 255, 255, 0.02);
  color: #64748b;
  border: 1px dashed rgba(255, 255, 255, 0.12);
  cursor: default;
}

.icon-svg {
  width: 14px;
  height: 14px;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .projects-section {
    padding: 55px 0;
  }
  .section-title {
    font-size: 1.6rem;
  }
  .projects-filter {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .filter-btn {
    flex: 1 1 calc(50% - 6px);
    text-align: center;
    padding: 9px 8px;
    font-size: 0.72rem;
  }
  .project-card {
    padding: 18px;
  }
  .project-actions {
    flex-direction: column;
    align-items: stretch;
    gap: 10px;
  }
  .action-btn {
    justify-content: center;
    width: 100%;
    padding: 11px 14px;
  }
}

@media (max-width: 400px) {
  .filter-btn {
    flex: 1 1 100%;
  }
}
</style>
