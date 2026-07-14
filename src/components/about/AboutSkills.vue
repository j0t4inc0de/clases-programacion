<script setup>
import { ref, computed } from 'vue'

const activeCategory = ref('backend')

const skillCategories = [
  { id: 'all', name: 'TODAS LAS COMPETENCIAS' },
  { id: 'backend', name: 'BACKEND & PYTHON' },
  { id: 'frontend', name: 'FRONTEND & UI/UX' },
  { id: 'devops', name: 'DEVOPS & LINUX SECOPS' },
  { id: 'db', name: 'BASES DE DATOS' },
]

const skillsList = [
  // BACKEND & PYTHON
  { name: 'Python 3', category: 'backend', level: 'Especialista', code: 'PY-01' },
  { name: 'Django & Django REST Framework', category: 'backend', level: 'Avanzado', code: 'DJ-01' },
  { name: 'FastAPI & Microservices Architecture', category: 'backend', level: 'Intermedio', code: 'FST-01' },
  { name: 'Biometría & Embeddings Facial IA', category: 'backend', level: 'Intermedio', code: 'AI-01' },
  { name: 'n8n Automation & Webhooks Engine', category: 'backend', level: 'Avanzado', code: 'N8N-01' },
  { name: 'Integración APIs REST & WebSockets', category: 'backend', level: 'Avanzado', code: 'API-01' },

  // FRONTEND & UI/UX
  { name: 'Vue.js 3 (Composition API / Setup)', category: 'frontend', level: 'Especialista', code: 'VUE-01' },
  { name: 'Pinia State Management', category: 'frontend', level: 'Avanzado', code: 'PIN-01' },
  { name: 'Tailwind CSS / Glassmorphism Architecture', category: 'frontend', level: 'Avanzado', code: 'CSS-01' },
  { name: 'JavaScript ES6+ / Asynchronous JS', category: 'frontend', level: 'Avanzado', code: 'JS-01' },
  { name: 'Vite Tooling & Performance Optimization', category: 'frontend', level: 'Avanzado', code: 'BLD-01' },
  { name: 'Dashboards IoT & UI en Tiempo Real', category: 'frontend', level: 'Especialista', code: 'IOT-01' },
  { name: 'HTML5 & Vanilla CSS3 Architecture', category: 'frontend', level: 'Avanzado', code: 'WEB-01' },

  // DEVOPS & INFRAESTRUCTURA
  { name: 'Linux Server (Ubuntu 24.04 LTS Administration)', category: 'devops', level: 'Avanzado', code: 'LNX-01' },
  { name: 'Docker & Docker Compose (+24 microservicios)', category: 'devops', level: 'Avanzado', code: 'DCK-01' },
  { name: 'Cloudflare Tunnels (Zero-Trust SSL/TLS Protection)', category: 'devops', level: 'Avanzado', code: 'CF-01' },
  { name: 'Tailscale Mesh VPN Architecture', category: 'devops', level: 'Avanzado', code: 'TS-01' },
  { name: 'Git & GitHub Version Control Architecture', category: 'devops', level: 'Avanzado', code: 'GIT-01' },

  // BASES DE DATOS
  { name: 'PostgreSQL Relational DB', category: 'db', level: 'Avanzado', code: 'PG-01' },
  { name: 'Redis (Caching & Async Workers)', category: 'db', level: 'Intermedio', code: 'RDS-01' },
  { name: 'SQLite & Query Optimization', category: 'db', level: 'Avanzado', code: 'SQL-01' },
  { name: 'Modelado Relacional & ORM', category: 'db', level: 'Avanzado', code: 'ORM-01' },
]

const filteredSkills = computed(() => {
  if (activeCategory.value === 'all') return skillsList
  return skillsList.filter(s => s.category === activeCategory.value)
})

const filterSkills = (catId) => {
  activeCategory.value = catId
}
</script>

<template>
  <section id="stack" class="skills-section">
    <div class="section-header-mono">
      <span class="section-number">02 / ARQUITECTURA</span>
      <h3 class="section-title">DOMINIO TECNOLÓGICO</h3>
      <p class="section-subtitle">
        Matriz técnica clasificada por capa de abstracción: desde el cliente reactivo en <strong>Vue.js 3</strong> hasta el servidor backend <strong>Python/Django</strong> y la infraestructura Linux en contenedores.
      </p>
    </div>

    <!-- Categorías Filtro -->
    <div class="skills-filter">
      <button
        v-for="cat in skillCategories"
        :key="cat.id"
        @click="filterSkills(cat.id)"
        class="filter-btn"
        :class="{ active: activeCategory === cat.id }"
      >
        {{ cat.name }}
      </button>
    </div>

    <!-- Grid de Habilidades Uniforme -->
    <div class="skills-grid">
      <div
        v-for="skill in filteredSkills"
        :key="skill.name"
        class="skill-card"
      >
        <div class="skill-code">{{ skill.code }}</div>
        <div class="skill-info">
          <div class="skill-header">
            <span class="skill-name">{{ skill.name }}</span>
            <span class="skill-badge" :class="skill.level.toLowerCase()">{{ skill.level }}</span>
          </div>
          <div class="skill-bar">
            <div class="skill-progress" :class="skill.level.toLowerCase()"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills-section {
  padding: 80px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.section-header-mono {
  margin-bottom: 48px;
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

.skills-filter {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 40px;
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

/* Skills Grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 16px;
}

.skill-card {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 20px;
  border-radius: 6px;
  background: rgba(255, 255, 255, 0.015);
  border: 1px solid rgba(255, 255, 255, 0.06);
  transition: all 0.25s ease;
}

.skill-card:hover {
  border-color: rgba(16, 185, 129, 0.5);
  background: rgba(16, 185, 129, 0.03);
}

.skill-code {
  font-family: monospace;
  font-size: 0.75rem;
  font-weight: 700;
  color: #64748b;
  padding: 6px 8px;
  background: rgba(255, 255, 255, 0.04);
  border-radius: 4px;
  min-width: 58px;
  text-align: center;
}

.skill-info {
  flex: 1;
  min-width: 0;
}

.skill-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 8px;
  gap: 8px;
}

.skill-name {
  font-weight: 700;
  font-size: 0.92rem;
  color: #ffffff;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.skill-badge {
  font-family: monospace;
  font-size: 0.68rem;
  font-weight: 700;
  padding: 2px 6px;
  border-radius: 3px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.skill-badge.avanzado, .skill-badge.especialista {
  background: rgba(16, 185, 129, 0.15);
  color: #10b981;
}

.skill-badge.intermedio {
  background: rgba(148, 163, 184, 0.15);
  color: #94a3b8;
}

.skill-bar {
  width: 100%;
  height: 4px;
  background: rgba(255, 255, 255, 0.06);
  border-radius: 2px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  border-radius: 2px;
}

.skill-progress.avanzado, .skill-progress.especialista {
  width: 92%;
  background: #10b981;
}

.skill-progress.intermedio {
  width: 75%;
  background: #64748b;
}

/* Responsive & Mobile-First ultra limpio para móvil */
@media (max-width: 640px) {
  .skills-section {
    padding: 55px 0;
  }
  .section-title {
    font-size: 1.65rem;
  }
  .skills-filter {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    gap: 8px;
    padding-bottom: 8px;
    margin-bottom: 24px;
    scrollbar-width: none;
  }
  .skills-filter::-webkit-scrollbar {
    display: none;
  }
  .filter-btn {
    flex: 0 0 auto;
    white-space: nowrap;
    padding: 8px 14px;
    font-size: 0.72rem;
    border-radius: 20px;
    background: rgba(255, 255, 255, 0.03);
  }
  .filter-btn.active {
    background: #10b981;
    color: #080a0f;
    box-shadow: 0 4px 14px rgba(16, 185, 129, 0.35);
  }

  /* Ocultamos código de skill y barra de carga en móvil para máxima limpieza */
  .skill-code,
  .skill-bar {
    display: none !important;
  }

  .skills-grid {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .skill-card {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 14px 18px;
    gap: 12px;
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.02);
    border: 1px solid rgba(255, 255, 255, 0.06);
  }
  .skill-info {
    width: 100%;
  }
  .skill-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0;
    gap: 8px;
  }
  .skill-name {
    font-size: 0.88rem;
    font-weight: 700;
    color: #f8fafc;
    white-space: normal;
    overflow: visible;
    text-overflow: unset;
    line-height: 1.3;
  }
  .skill-badge {
    font-size: 0.66rem;
    padding: 3px 8px;
    border-radius: 4px;
    flex-shrink: 0;
  }
}

@media (max-width: 380px) {
  .skill-card {
    padding: 12px 14px;
    gap: 8px;
  }
  .skill-name {
    font-size: 0.82rem;
  }
}
</style>
