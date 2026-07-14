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
    code: 'PROJ-01',
    title: 'Telemetrics — Dashboard IoT en Tiempo Real',
    role: 'Ingeniero de Software Frontend',
    company: 'Soluciones Tecnológicas Netzona Spa',
    period: 'May. 2026 - Actualidad',
    category: 'iot',
    featured: true,
    description: 'Plataforma web (Dashboard) orientada a la visualización ininterrumpida de datos críticos provenientes de sensores y dispositivos IoT en terreno. Estandariza múltiples fuentes y protocolos en una interfaz única, rápida y personalizable.',
    impact: 'Resolución de la privacidad y compartimentación de datos industriales mediante una arquitectura granular de control de acceso jerárquico basada en roles (Técnico, Administrador y Trabajador).',
    tags: ['Vue.js 3', 'IoT Architecture', 'Real-Time Data', 'REST APIs', 'RBAC Security', 'Tailwind CSS'],
    liveUrl: null,
    githubUrl: null,
    status: 'EN PRODUCCIÓN / INTERNO'
  },
  {
    id: 'efibox',
    code: 'PROJ-02',
    title: 'EFIBOX Industrial Dashboard',
    role: 'Ingeniero en Informática — Encargado Frontend',
    company: 'Efintel Ltda.',
    period: 'Jul. 2025 - Mar. 2026',
    category: 'iot',
    featured: true,
    description: 'Diseño, implementación y evolución estratégica de soluciones frontend para la plataforma industrial EFIBOX orientada al monitoreo y control operacional de dispositivos IoT en tiempo real.',
    impact: 'Optimización en el renderizado de tablas dinámicas con alto volumen de registros, exportación nativa de reportes a PDF/Excel, integración con APIs REST para gestión de alertas tempranas y presentación ejecutiva de KPIs.',
    tags: ['Vue.js 3', 'Composition API', 'JavaScript ES6+', 'APIs REST', 'Data Visualization', 'Export PDF/Excel'],
    liveUrl: null,
    githubUrl: null,
    status: 'PLATAFORMA INDUSTRIAL'
  },
  {
    id: 'linux-cloud',
    code: 'PROJ-03',
    title: 'Cloud Privada & Microservicios (Linux Server Zero-Trust)',
    role: 'DevOps & Arquitecto de Infraestructura',
    company: 'Infraestructura Propia 24/7',
    period: 'Abr. 2026 - Actualidad',
    category: 'saas',
    featured: true,
    description: 'Arquitectura diseñada, desplegada y administrada en servidor propio Ubuntu 24.04 LTS para hospedar bases de datos, microservicios y automatizaciones empresariales operando con alta disponibilidad.',
    impact: 'Orquestación activa de +24 servicios con Docker Compose (PostgreSQL, SQLite, Redis, n8n, APIs Django/FastAPI y apps Vue). Seguridad Zero-Trust mediante Cloudflare Tunnels (SSL/TLS en el edge) y acceso administrativo SSH exclusivamente vía red Mesh VPN con Tailscale. Ajustes avanzados de kernel (Page Cache en RAM) para maximizar IOPS en unidades SSD.',
    tags: ['DevOps', 'Ubuntu 24.04 LTS', 'Docker Compose', 'Cloudflare Tunnels', 'Tailscale VPN', 'PostgreSQL', 'Redis'],
    liveUrl: null,
    githubUrl: null,
    status: 'INFRAESTRUCTURA ACTIVA'
  },
  {
    id: 'cleanmail',
    code: 'PROJ-04',
    title: 'CleanMail — Micro-SaaS de Verificación Masiva de Emails',
    role: 'Full-Stack Engineer & SecOps',
    company: 'SaaS Propio con Pasarela de Pagos',
    period: 'Jun. 2026',
    category: 'saas',
    featured: true,
    description: 'Plataforma diseñada y construida de principio a fin para depurar y validar listas masivas de correos electrónicos a alta velocidad con pasarela de pagos integrada para transacciones globales.',
    impact: 'Backend asíncrono de alto rendimiento con Django 5 REST Framework, PostgreSQL y Redis + Gunicorn + Workers, capaz de procesar en paralelo miles de registros sin bloquear la API. Pipeline en 3 capas: Sintaxis RFC 5322, filtrado de +200 dominios desechables y resolución DNS de registros MX. Frontend en Vue.js 3 y Vite con autenticación Passwordless mediante Magic Links.',
    tags: ['Vue.js 3', 'Pinia', 'Django 5 REST', 'Redis Workers', 'PostgreSQL', 'Magic Links JWT', 'n8n Webhooks'],
    liveUrl: null,
    githubUrl: 'https://github.com/j0t4inc0de/j0tainc0de',
    status: 'MICRO-SAAS'
  },
  {
    id: 'smartlend',
    code: 'PROJ-05',
    title: 'SmartLend — Tótem con Biometría Facial e IA (INACAP)',
    role: 'Desarrollador Full-Stack & AI Integration',
    company: 'INACAP Sede Los Ángeles',
    period: 'Ago. 2023 - Jul. 2026',
    category: 'ai',
    featured: true,
    description: 'Ecosistema Full-Stack impulsado por Inteligencia Artificial para automatizar el préstamo seguro y expedito de equipamiento técnico a alumnos y docentes integrado en un tótem físico táctil.',
    impact: 'Motor de reconocimiento facial biométrico en Python que identifica personas en milisegundos utilizando embeddings vectoriales (sin almacenar imágenes sensibles para garantizar la privacidad). API con Django REST Framework y frontend reactivo con Vue.js 3 y Pinia mostrando feed de verificación en vivo e inventario de laboratorio.',
    tags: ['Python IA / Biometría', 'Vue.js 3', 'Pinia', 'Django REST Framework', 'Embeddings', 'Tótem Táctil'],
    liveUrl: null,
    githubUrl: 'https://github.com/j0t4inc0de/j0tainc0de',
    status: 'PROYECTO ACADÉMICO'
  },
  {
    id: 'wearesamod',
    code: 'PROJ-06',
    title: 'We Are Samod — Plataforma Cloud & SaaS Ecosystem',
    role: 'Lead Frontend Developer',
    company: 'We Are Samod',
    period: 'Abr. 2026 - Actualidad',
    category: 'saas',
    featured: false,
    description: 'Desarrollo del frontend principal para la iniciativa enfocada en automatización inteligente, ciberseguridad defensiva y microservicios cloud.',
    impact: 'Sistema de diseño minimalista, tipografía clara (Inter & Outfit) y micro-animaciones fluidas. SPA de alta velocidad en Vue 3 y TailwindCSS con enrutamiento dinámico y optimización SEO en el cliente.',
    tags: ['Vue 3', 'Tailwind CSS', 'SPA Architecture', 'Micro-animaciones', 'Performance'],
    liveUrl: 'https://wearesamod.com',
    githubUrl: null,
    status: 'EN PRODUCCIÓN'
  },
  {
    id: 'asesorats',
    code: 'PROJ-07',
    title: 'Asesora TS — CRM & Sistema de Gestión Empresarial',
    role: 'Python/Django Backend & Full-Stack Developer',
    company: 'Asesora TS',
    period: 'Mar. 2026 - Abr. 2026',
    category: 'saas',
    featured: false,
    description: 'Sistema integral para administración de expedientes, flujos de asesoría, documentación y seguimiento de casos para consultoría empresarial.',
    impact: 'Modelado relacional con Django ORM sobre PostgreSQL/SQLite. Seguridad y control de acceso granular RBAC para consultores, administradores y clientes con arquitectura limpia MVC/MVT.',
    tags: ['Python', 'Django ORM', 'PostgreSQL', 'RBAC Security', 'MVC/MVT Architecture'],
    liveUrl: null,
    githubUrl: null,
    status: 'EN PRODUCCIÓN'
  },
  {
    id: 'desafiatp',
    code: 'PROJ-08',
    title: 'Olimpiadas Tecnológicas DesafíaT-TP 2025',
    role: 'Desarrollador Web & Coordinador Técnico-Educativo',
    company: 'Liceo Bicentenario Tecnológico El Huertón',
    period: 'Mar. 2025 - Jul. 2025',
    category: 'ai',
    featured: false,
    description: 'Plataforma oficial para evento tecnológico provincial que integró a 15 liceos técnico-profesionales, automatizando inscripciones, rankings y evaluaciones.',
    impact: 'Sitio institucional en WordPress con alto estándar UX/UI, integración con Moodle para capacitación online y desarrollo de chatbot interactivo con IA vía OpenAI para asistencia técnica instantánea.',
    tags: ['WordPress UX/UI', 'Moodle Integration', 'OpenAI Chatbot', 'HTML/CSS/JS', 'EdTech'],
    liveUrl: null,
    githubUrl: null,
    status: 'EVENTO COMPLETADO'
  },
  {
    id: 'hogar4patas',
    code: 'PROJ-09',
    title: 'Hogar de 4 Patas — Plataforma de Rescate Animal',
    role: 'Full-Stack Developer',
    company: 'Asociado con INACAP',
    period: 'Oct. 2023',
    category: 'ai',
    featured: false,
    description: 'Plataforma web y orientada a dispositivos móviles con el propósito de optimizar el rescate y reporte de animales en situación de calle.',
    impact: 'Desarrollada con Django, Python, JavaScript y CSS para permitir reportes geolocalizados en tiempo real, administración de hogares temporales y gestión de donaciones ciudadanas.',
    tags: ['Django', 'Python 3', 'JavaScript', 'HTML5 & CSS3', 'Social Impact'],
    liveUrl: null,
    githubUrl: 'https://github.com/j0t4inc0de/j0tainc0de',
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
        Análisis técnico de plataformas en producción: desde visualización IoT de misión crítica hasta microservicios asíncronos y servidores Linux orquestados.
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

    <!-- Grid de Proyectos -->
    <div class="projects-grid">
      <div
        v-for="proj in filteredProjects"
        :key="proj.id"
        class="project-card"
        :class="{ 'card-featured': proj.featured }"
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

        <p class="project-desc">{{ proj.description }}</p>
        
        <div class="project-impact-box">
          <div class="impact-title">ARQUITECTURA & SOLUCIÓN:</div>
          <p class="impact-text">{{ proj.impact }}</p>
        </div>

        <!-- Tags -->
        <div class="project-tags">
          <span v-for="tag in proj.tags" :key="tag" class="tech-tag">
            {{ tag }}
          </span>
        </div>

        <!-- Enlaces -->
        <div class="project-actions" v-if="proj.githubUrl || proj.liveUrl">
          <a v-if="proj.githubUrl" :href="proj.githubUrl" target="_blank" rel="noopener noreferrer" class="action-btn github-btn">
            <svg class="icon-svg" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.87 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2Z"/>
            </svg>
            <span>Ver Repositorio GitHub</span>
          </a>
          <a v-if="proj.liveUrl" :href="proj.liveUrl" target="_blank" rel="noopener noreferrer" class="action-btn live-btn">
            <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
            </svg>
            <span>Sitio Web Oficial</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: 80px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.section-header-mono {
  margin-bottom: 48px;
  max-width: 780px;
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

.section-title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 14px;
  letter-spacing: -0.02em;
}

.section-subtitle {
  font-size: 1.05rem;
  color: #94a3b8;
  line-height: 1.7;
}

.projects-filter {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 44px;
}

.filter-btn {
  padding: 8px 18px;
  background: rgba(255, 255, 255, 0.02);
  color: #64748b;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 4px;
  font-family: monospace;
  font-size: 0.78rem;
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

/* Projects Grid */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(360px, 1fr));
  gap: 24px;
}

.project-card {
  display: flex;
  flex-direction: column;
  padding: 28px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.015);
  border: 1px solid rgba(255, 255, 255, 0.07);
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  position: relative;
}

.project-card:hover {
  transform: translateY(-4px);
  border-color: rgba(16, 185, 129, 0.4);
  box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.6);
}

.card-featured {
  border-top: 2px solid #10b981;
}

.project-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 12px;
  margin-bottom: 14px;
}

.project-meta-left {
  display: flex;
  align-items: center;
  gap: 8px;
}

.project-code {
  font-family: monospace;
  font-size: 0.72rem;
  font-weight: 700;
  color: #10b981;
  padding: 2px 6px;
  background: rgba(16, 185, 129, 0.1);
  border-radius: 3px;
}

.project-company {
  font-size: 0.82rem;
  font-weight: 700;
  color: #e2e8f0;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.project-status {
  font-family: monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #64748b;
  padding: 3px 8px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 3px;
}

.project-title {
  font-size: 1.3rem;
  font-weight: 800;
  color: #ffffff;
  line-height: 1.35;
  margin-bottom: 6px;
}

.project-role {
  font-size: 0.85rem;
  color: #94a3b8;
  font-weight: 600;
  margin-bottom: 16px;
}

.project-desc {
  font-size: 0.93rem;
  line-height: 1.65;
  color: #94a3b8;
  margin-bottom: 16px;
}

.project-impact-box {
  background: rgba(255, 255, 255, 0.02);
  border-left: 2px solid #10b981;
  padding: 12px 16px;
  border-radius: 0 4px 4px 0;
  margin-bottom: 20px;
}

.impact-title {
  font-family: monospace;
  font-size: 0.75rem;
  font-weight: 700;
  color: #10b981;
  margin-bottom: 4px;
  letter-spacing: 0.04em;
}

.impact-text {
  font-size: 0.86rem;
  line-height: 1.55;
  color: #e2e8f0;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 24px;
  margin-top: auto;
}

.tech-tag {
  font-family: monospace;
  font-size: 0.75rem;
  font-weight: 600;
  padding: 4px 8px;
  border-radius: 3px;
  background: rgba(255, 255, 255, 0.04);
  color: #94a3b8;
  border: 1px solid rgba(255, 255, 255, 0.06);
}

.project-actions {
  display: flex;
  gap: 12px;
  padding-top: 18px;
  border-top: 1px solid rgba(255, 255, 255, 0.06);
}

.action-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 0.84rem;
  font-weight: 600;
  padding: 8px 14px;
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

.icon-svg {
  width: 15px;
  height: 15px;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>
