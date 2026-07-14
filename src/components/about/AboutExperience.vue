<script setup>
const experienceList = [
  {
    code: 'EXP-01',
    role: 'Ingeniero de Software Frontend',
    company: 'Soluciones Tecnológicas Netzona Spa',
    period: 'May. 2026 - Actualidad',
    location: 'Viña del Mar / En remoto',
    details: 'Desarrollo integral del sistema Telemetrics (Dashboard IoT en tiempo real). Centralización de datos complejos de sensores en terreno y diseño de arquitectura de permisos por roles (RBAC).'
  },
  {
    code: 'EXP-02',
    role: 'Ingeniero en Informática – Encargado Frontend',
    company: 'Efintel Ltda.',
    period: 'Ene. 2026 - Mar. 2026',
    location: 'Los Ángeles / En remoto',
    details: 'Liderazgo en el diseño e implementación frontend de la plataforma industrial EFIBOX. Integración de APIs REST, optimización de tablas dinámicas con exportación PDF/Excel, visualización de KPIs y reportes QA.'
  },
  {
    code: 'EXP-03',
    role: 'Analista Programador - Frontend',
    company: 'Efintel Ltda.',
    period: 'Jun. 2025 - Nov. 2025',
    location: 'Concepción / En remoto',
    details: 'Desarrollo frontend con Vue.js 3 y diseño responsivo con Tailwind CSS para la plataforma de monitoreo industrial. Creación de componentes modulares y alertas en tiempo real.'
  },
  {
    code: 'EXP-04',
    role: 'Desarrollador Web Principal & Coordinador Técnico',
    company: 'Olimpiadas Tecnológicas DesafíaT-TP 2025',
    period: 'Mar. 2025 - Jul. 2025',
    location: 'Los Ángeles / Presencial',
    details: 'Desarrollador principal de la plataforma oficial para evento de 15 liceos técnico-profesionales. Integración de WordPress con Moodle para capacitación online y chatbot asistido con IA de OpenAI.'
  },
  {
    code: 'EXP-05',
    role: 'Servicio de Ayudantía en Base de Datos Relacionales',
    company: 'Universidad Tecnológica de Chile, INACAP',
    period: 'Sep. 2023 - Dic. 2023',
    location: 'Los Ángeles / Presencial',
    details: 'Apoyo pedagógico y técnico en optimización de consultas SQL, modelado de bases de datos relacionales y resolución de algoritmos.'
  }
]

const educationList = [
  {
    code: 'EDU-01',
    degree: 'Ingeniería en Informática (Titulado)',
    institution: 'Universidad Tecnológica de Chile, INACAP',
    period: 'Mar. 2022 – Ene. 2026',
    badge: 'SELLO DE INNOVACIÓN 2025 DAE',
    details: 'Formación de alto nivel en ingeniería de software, arquitectura web, bases de datos relacionales, metodologías ágiles y gestión de proyectos informáticos.'
  },
  {
    code: 'EDU-02',
    degree: 'Bootcamp Agentes de Cambio — Gestión de Proyectos',
    institution: 'INACAP (Grupo de Innovación Social)',
    period: 'Jul. 2025',
    badge: 'CERTIFICADO DE PARTICIPACIÓN',
    details: 'Capacitación en liderazgo, comunicación estratégica y diseño de soluciones con impacto basado en los Objetivos de Desarrollo Sostenible (ODS).'
  },
  {
    code: 'EDU-03',
    degree: 'PCAP: Programming Essentials in Python',
    institution: 'Cisco Networking Academy & Python Institute',
    period: 'Ago. 2023 – Ene. 2024',
    badge: 'CERTIFICACIÓN OFICIAL CISCO',
    details: 'Dominio de estructuras de datos, programación orientada a objetos (POO), manejo de excepciones y algoritmos computacionales en Python.'
  },
  {
    code: 'EDU-04',
    degree: 'Títulos Intermedios & Certificaciones Curriculares',
    institution: 'Universidad Tecnológica de Chile, INACAP',
    period: '2022 – 2025',
    badge: 'MÚLTIPLES CERTIFICACIONES',
    details: '• Desarrollador Full Stack (Django/CSS)\n• Diseño y Gestión de Base de Datos (SQL)\n• Analista Programador Titulado\n• Soporte Computacional'
  }
]
</script>

<template>
  <section id="trayectoria" class="experience-section">
    <div class="section-header-mono">
      <span class="section-number">04 / TRAYECTORIA</span>
      <h3 class="section-title">HISTORICAL TRACK RECORD</h3>
      <p class="section-subtitle">
        Evolución profesional continuada: experiencia en empresas tecnológicas de telemetría IoT e historial académico de excelencia.
      </p>
    </div>

    <div class="timeline-container">
      <!-- Columna Experiencia -->
      <div class="timeline-col">
        <div class="col-header">
          <span class="col-indicator"></span>
          <h4>EXPERIENCIA LABORAL</h4>
        </div>

        <div class="timeline-list">
          <div v-for="exp in experienceList" :key="exp.code" class="timeline-card">
            <div class="card-top">
              <span class="item-code">{{ exp.code }}</span>
              <span class="item-period">{{ exp.period }}</span>
            </div>
            <h5 class="item-role">{{ exp.role }}</h5>
            <div class="item-company">{{ exp.company }} &middot; <span class="item-loc">{{ exp.location }}</span></div>
            <p class="item-desc">{{ exp.details }}</p>
          </div>
        </div>
      </div>

      <!-- Columna Educación -->
      <div class="timeline-col">
        <div class="col-header">
          <span class="col-indicator edu-indicator"></span>
          <h4>FORMACIÓN & CERTIFICACIONES</h4>
        </div>

        <div class="timeline-list">
          <div v-for="edu in educationList" :key="edu.code" class="timeline-card">
            <div class="card-top">
              <span class="item-code edu-code">{{ edu.code }}</span>
              <span class="item-period">{{ edu.period }}</span>
            </div>
            <div class="badge-row">
              <span class="edu-badge">{{ edu.badge }}</span>
            </div>
            <h5 class="item-role">{{ edu.degree }}</h5>
            <div class="item-company">{{ edu.institution }}</div>
            <p class="item-desc whitespace-pre-line">{{ edu.details }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  padding: 80px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.section-header-mono {
  margin-bottom: 56px;
  max-width: 760px;
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

.timeline-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}

.timeline-col {
  display: flex;
  flex-direction: column;
}

.col-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 32px;
  padding-bottom: 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.col-indicator {
  width: 10px;
  height: 10px;
  background: #10b981;
  border-radius: 2px;
}

.edu-indicator {
  background: #38bdf8;
}

.col-header h4 {
  font-family: monospace;
  font-size: 1rem;
  font-weight: 800;
  color: #ffffff;
  letter-spacing: 0.06em;
}

.timeline-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.timeline-card {
  padding: 24px;
  background: rgba(255, 255, 255, 0.015);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 6px;
  transition: all 0.25s ease;
}

.timeline-card:hover {
  border-color: rgba(255, 255, 255, 0.2);
  background: rgba(255, 255, 255, 0.03);
}

.card-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.item-code {
  font-family: monospace;
  font-size: 0.72rem;
  font-weight: 700;
  color: #10b981;
  padding: 2px 6px;
  background: rgba(16, 185, 129, 0.1);
  border-radius: 3px;
}

.edu-code {
  color: #38bdf8;
  background: rgba(56, 189, 248, 0.1);
}

.item-period {
  font-family: monospace;
  font-size: 0.78rem;
  color: #94a3b8;
  font-weight: 600;
}

.badge-row {
  margin-bottom: 10px;
}

.edu-badge {
  font-family: monospace;
  font-size: 0.7rem;
  font-weight: 700;
  padding: 3px 8px;
  background: rgba(16, 185, 129, 0.15);
  color: #10b981;
  border-radius: 3px;
  letter-spacing: 0.04em;
}

.item-role {
  font-size: 1.15rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 4px;
  line-height: 1.3;
}

.item-company {
  font-size: 0.88rem;
  font-weight: 600;
  color: #e2e8f0;
  margin-bottom: 12px;
}

.item-loc {
  color: #64748b;
  font-weight: 400;
}

.item-desc {
  font-size: 0.9rem;
  line-height: 1.65;
  color: #94a3b8;
}

.whitespace-pre-line {
  white-space: pre-line;
}

@media (max-width: 992px) {
  .timeline-container {
    grid-template-columns: 1fr;
    gap: 40px;
  }
}

@media (max-width: 640px) {
  .experience-section {
    padding: 60px 0;
  }
  .section-title {
    font-size: 1.6rem;
  }
  .timeline-card {
    padding: 18px;
    border-left-width: 2px;
  }
  .item-role {
    font-size: 1.05rem;
  }
  .item-desc {
    font-size: 0.86rem;
  }
}

@media (max-width: 400px) {
  .card-top {
    flex-direction: column;
    align-items: flex-start;
    gap: 6px;
  }
}
</style>
