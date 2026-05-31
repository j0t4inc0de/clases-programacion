<script setup>
import { ref, onMounted } from 'vue'

defineProps({
  whatsappLink: {
    type: String,
    required: true
  }
})

const terminalLines = ref([
  { text: '# Cargando entorno de aprendizaje...', type: 'comment' },
  { text: '>>> estudiante = Estudiante(nombre="Tú")', type: 'input' },
  { text: '>>> estudiante.agregar_habilidad("Lógica de Programación")', type: 'input' },
  { text: '¡Entendiendo condicionales y ciclos!', type: 'output' },
  { text: '>>> tutor = JuanErices()', type: 'input' },
  { text: '>>> tutor.explicar("PSeInt", paso_a_paso=True)', type: 'input' },
  { text: '[Paso 1] Escribir "Hola Mundo"', type: 'success' },
  { text: '[Paso 2] Definir variables de forma simple', type: 'success' },
  { text: '>>> # ¡Felicidades! Has aprobado tu examen. [Aprobado]', type: 'comment' }
])

const visibleLines = ref([])

onMounted(() => {
  let index = 0
  const addLine = () => {
    if (index < terminalLines.value.length) {
      visibleLines.value.push(terminalLines.value[index])
      index++
      setTimeout(addLine, index === 1 ? 1200 : index === 4 ? 1500 : 800)
    } else {
      // Loop after some time
      setTimeout(() => {
        visibleLines.value = []
        index = 0
        addLine()
      }, 5000)
    }
  }
  addLine()
})
</script>

<template>
  <section class="hero-section">
    <!-- Abstract gradient backgrounds for premium glow -->
    <div class="glow-orb orb-1"></div>
    <div class="glow-orb orb-2"></div>

    <div class="container hero-container">
      <div class="hero-content">
        <span class="hero-badge">
          <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" style="display:inline-block; vertical-align:middle; margin-right:6px; margin-top:-2px;">
            <rect x="2" y="3" width="20" height="14" rx="2" ry="2"></rect>
            <line x1="8" y1="21" x2="16" y2="21"></line>
            <line x1="12" y1="17" x2="12" y2="21"></line>
          </svg>
          Clases Personalizadas 1-a-1
        </span>
        <h1 class="hero-title">
          Clases particulares de <span class="highlight-text">programación</span> para estudiantes
        </h1>
        <p class="hero-subtitle">
          Aprende PSeInt, Python y lógica de programación paso a paso, con ejercicios adaptados a tu nivel. Pierde el miedo al código y asegura tus notas.
        </p>
        <div class="hero-actions">
          <a :href="whatsappLink" target="_blank" rel="noopener noreferrer" class="btn btn-whatsapp pulse-btn">
            <!-- WhatsApp Icon -->
            <svg class="icon-svg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" fill="currentColor">
              <path d="M380.9 97.1C339 55.1 283.2 32 223.9 32c-122.4 0-222 99.6-222 222 0 39.1 10.2 77.3 29.6 111L3 480l117.7-30.9c32.4 17.7 68.9 27 106.1 27h.1c122.3 0 224.1-99.6 224.1-222 0-59.3-25.2-115-67.1-157zm-157 341.6c-33.2 0-65.7-8.9-94-25.7l-6.7-4-69.8 18.3L72 359.2l-4.4-7c-18.5-29.4-28.2-63.3-28.2-98.2 0-101.7 82.8-184.5 184.6-184.5 49.3 0 95.6 19.2 130.4 54.1 34.8 34.9 56.2 81.2 56.1 130.5 0 101.8-84.9 184.6-186.6 184.6zm101.2-138.2c-5.5-2.8-32.8-16.2-37.9-18-5.1-1.9-8.8-2.8-12.5 2.8-3.7 5.6-14.3 18-17.6 21.8-3.2 3.7-6.5 4.2-12 1.4-32.6-16.3-54-29.1-75.5-66-5.7-9.8 5.7-9.1 16.3-30.3 1.8-3.7.9-6.9-.5-9.7-1.4-2.8-12.5-30.1-17.1-41.2-4.5-10.8-9.1-9.3-12.5-9.5-3.2-.2-6.9-.2-10.6-.2-3.7 0-9.7 1.4-14.8 6.9-5.1 5.6-19.4 19-19.4 46.3 0 27.3 19.9 53.7 22.6 57.4 2.8 3.7 39.1 59.7 94.8 83.8 35.2 15.2 49 16.5 66.6 13.9 10.7-1.6 32.8-13.4 37.4-26.4 4.6-13 4.6-24.1 3.2-26.4-1.3-2.5-5-3.9-10.5-6.6z"/>
            </svg>
            Agendar clase por WhatsApp
          </a>
          <a href="#metodo" class="btn btn-secondary">
            Ver cómo trabajo
          </a>
        </div>
        
        <div class="hero-trust-minors">
          <div class="trust-minor-item">
            <span class="bullet">✓</span> Sin contratos fijos
          </div>
          <div class="trust-minor-item">
            <span class="bullet">✓</span> Clases 100% prácticas
          </div>
          <div class="trust-minor-item">
            <span class="bullet">✓</span> Material a tu medida
          </div>
        </div>
      </div>

      <div class="hero-visual">
        <div class="terminal-mockup glass-panel">
          <div class="terminal-header">
            <div class="terminal-dots">
              <span class="dot red"></span>
              <span class="dot yellow"></span>
              <span class="dot green"></span>
            </div>
            <div class="terminal-title">juan_erices.py</div>
            <div class="terminal-status">online</div>
          </div>
          <div class="terminal-body">
            <TransitionGroup name="terminal-fade">
              <div 
                v-for="(line, index) in visibleLines" 
                :key="index" 
                class="terminal-line"
                :class="line.type"
              >
                {{ line.text }}
              </div>
            </TransitionGroup>
            <div class="terminal-cursor"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  padding-top: 160px; /* Offset fixed header */
  padding-bottom: 90px;
  overflow: hidden;
  background: radial-gradient(circle at 10% 20%, rgba(14, 165, 233, 0.03) 0%, transparent 40%),
              radial-gradient(circle at 90% 80%, rgba(16, 185, 129, 0.02) 0%, transparent 45%);
}

.hero-container {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 48px;
  align-items: center;
}

.hero-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.hero-badge {
  display: inline-block;
  padding: 6px 14px;
  background-color: var(--accent-glow);
  color: var(--accent);
  font-family: var(--font-heading);
  font-weight: 700;
  font-size: 0.85rem;
  border-radius: 50px;
  margin-bottom: 24px;
  border: 1px solid rgba(var(--accent-rgb), 0.15);
}

.hero-title {
  font-size: 3.5rem;
  line-height: 1.15;
  letter-spacing: -0.02em;
  margin-bottom: 20px;
}

.highlight-text {
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-green) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-subtitle {
  font-size: 1.2rem;
  color: var(--text-secondary);
  margin-bottom: 36px;
  max-width: 580px;
  line-height: 1.6;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  margin-bottom: 36px;
}

.icon-svg {
  width: 18px;
  height: 18px;
}

.hero-trust-minors {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.trust-minor-item {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 0.9rem;
  color: var(--text-secondary);
  font-weight: 500;
}

.trust-minor-item .bullet {
  color: var(--accent-green);
  font-weight: bold;
}

/* Glow orbs */
.glow-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  z-index: -1;
  opacity: 0.35;
}

.orb-1 {
  top: 10%;
  left: -5%;
  width: 300px;
  height: 300px;
  background-color: rgba(var(--accent-rgb), 0.15);
}

.orb-2 {
  bottom: 20%;
  right: 5%;
  width: 250px;
  height: 250px;
  background-color: rgba(var(--accent-green-rgb), 0.08);
}

/* Terminal Mockup */
.terminal-mockup {
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 30px 60px -15px rgba(0, 0, 0, 0.6);
  border: 1px solid var(--border-color);
}

.terminal-header {
  height: 40px;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 16px;
  border-bottom: 1px solid var(--border-color);
}

.terminal-dots {
  display: flex;
  gap: 6px;
}

.terminal-dots .dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
}

.terminal-dots .red { background-color: #ef4444; }
.terminal-dots .yellow { background-color: #f59e0b; }
.terminal-dots .green { background-color: #10b981; }

.terminal-title {
  font-family: var(--font-sans);
  font-size: 0.8rem;
  color: var(--text-secondary);
}

.terminal-status {
  font-size: 0.75rem;
  color: var(--accent-green);
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 4px;
}

.terminal-status::before {
  content: '';
  display: inline-block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: var(--accent-green);
  box-shadow: 0 0 8px var(--accent-green);
}

.terminal-body {
  background-color: rgba(5, 7, 13, 0.95);
  padding: 24px;
  min-height: 280px;
  font-family: 'Courier New', Courier, monospace;
  font-size: 0.9rem;
  display: flex;
  flex-direction: column;
  gap: 8px;
  line-height: 1.5;
  text-align: left;
}

.terminal-line {
  color: #fff;
  word-break: break-word;
}

.terminal-line.comment { color: #57606a; font-style: italic; }
.terminal-line.input { color: #f8fafc; }
.terminal-line.output { color: var(--accent); }
.terminal-line.success { color: var(--accent-green); }

.terminal-cursor {
  display: inline-block;
  width: 8px;
  height: 15px;
  background-color: var(--accent);
  animation: blink 1s step-end infinite;
  margin-top: 4px;
}

@keyframes blink {
  50% { opacity: 0; }
}

/* Animations */
.terminal-fade-enter-active,
.terminal-fade-leave-active {
  transition: all 0.4s ease;
}
.terminal-fade-enter-from {
  opacity: 0;
  transform: translateY(8px);
}
.terminal-fade-leave-to {
  opacity: 0;
}

@media (max-width: 992px) {
  .hero-container {
    grid-template-columns: 1fr;
    gap: 40px;
    text-align: center;
  }
  .hero-content {
    align-items: center;
  }
  .hero-title {
    font-size: 2.8rem;
  }
  .hero-subtitle {
    margin-left: auto;
    margin-right: auto;
  }
  .hero-actions {
    justify-content: center;
  }
  .hero-trust-minors {
    justify-content: center;
  }
}

@media (max-width: 576px) {
  .hero-section {
    padding-top: 110px;
  }
  .hero-title {
    font-size: 2.2rem;
  }
  .hero-actions {
    flex-direction: column;
    width: 100%;
  }
  .hero-actions .btn {
    width: 100%;
  }
}
</style>
