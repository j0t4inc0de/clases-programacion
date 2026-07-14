<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const showContactPopup = ref(false)
let popupTimer = null

const handleScroll = () => {
  isScrolled.value = window.scrollY > 40
}

const dismissPopup = () => {
  showContactPopup.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  
  // Activar popup de disponibilidad inmediata a los 10 segundos exactos
  popupTimer = setTimeout(() => {
    showContactPopup.value = true
  }, 10000)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  if (popupTimer) clearTimeout(popupTimer)
})
</script>

<template>
  <nav class="portfolio-nav" :class="{ 'nav-scrolled': isScrolled }">
    <div class="nav-container">
      <div class="nav-brand">
        <span class="brand-code">JE /</span>
        <span class="brand-title">JUAN ERICES FUENTEALBA</span>
        <span class="brand-tag">SOFTWARE ENGINEER</span>
      </div>

      <div class="nav-menu">
        <a href="#perfil" class="nav-link"><span class="link-num">01.</span> PERFIL</a>
        <a href="#stack" class="nav-link"><span class="link-num">02.</span> ARQUITECTURA</a>
        <a href="#proyectos" class="nav-link"><span class="link-num">03.</span> CASE STUDIES</a>
        <a href="#trayectoria" class="nav-link"><span class="link-num">04.</span> TRAYECTORIA</a>
        
        <div class="nav-contact-wrapper">
          <a href="#contacto" class="nav-link contact-glow-btn"><span class="link-num">05.</span> CONTACTO</a>

          <Transition name="popup-fade">
            <div v-if="showContactPopup" class="contact-navbar-popup">
              <div class="popup-arrow"></div>
              <div class="popup-content">
                <div class="popup-status-row">
                  <span class="status-dot-pulse"></span>
                  <span class="status-label">NOTIFICACIÓN DE DISPONIBILIDAD</span>
                </div>
                <p class="popup-message">
                  ¡Hola! Cuento con <strong>disponibilidad inmediata</strong> para integrarme a tu equipo técnico o proyecto informático.
                </p>
                <div class="popup-actions">
                  <a href="#contacto" @click="dismissPopup" class="btn-popup-cta">Ver Datos & Agendar →</a>
                  <button @click="dismissPopup" class="btn-popup-close" title="Cerrar notificación">×</button>
                </div>
              </div>
            </div>
          </Transition>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.portfolio-nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 76px;
  z-index: 100;
  background: rgba(8, 10, 15, 0.75);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.portfolio-nav.nav-scrolled {
  height: 64px;
  background: rgba(8, 10, 15, 0.92);
  border-bottom: 1px solid rgba(255, 255, 255, 0.12);
  box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.7);
}

.nav-container {
  max-width: 1360px;
  height: 100%;
  margin: 0 auto;
  padding: 0 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-brand {
  display: flex;
  align-items: center;
  gap: 12px;
  font-family: var(--font-heading);
  letter-spacing: 0.05em;
  margin-right: auto;
  padding-right: 40px;
}

.brand-code {
  font-family: monospace;
  font-weight: 700;
  color: #10b981;
  font-size: 1.1rem;
}

.brand-title {
  font-weight: 800;
  font-size: 0.95rem;
  color: #ffffff;
}

.brand-tag {
  font-size: 0.72rem;
  font-weight: 600;
  padding: 3px 10px;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: #94a3b8;
  border-radius: 4px;
  margin-left: 4px;
}

.nav-menu {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav-link {
  font-size: 0.82rem;
  font-weight: 600;
  color: #94a3b8;
  letter-spacing: 0.08em;
  text-decoration: none;
  transition: color 0.25s ease;
  position: relative;
  padding: 6px 0;
}

.link-num {
  font-family: monospace;
  color: #10b981;
  font-size: 0.78rem;
  margin-right: 4px;
}

.nav-link:hover {
  color: #ffffff;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: #10b981;
  transition: width 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.nav-link:hover::after {
  width: 100%;
}

.contact-glow-btn {
  color: #10b981 !important;
  font-weight: 700;
  padding: 6px 14px !important;
  border-radius: 4px;
  border: 1px solid rgba(16, 185, 129, 0.3);
  background: rgba(16, 185, 129, 0.08);
  animation: attention-pulse 4.5s infinite cubic-bezier(0.4, 0, 0.6, 1);
}

.contact-glow-btn::after {
  display: none !important;
}

@keyframes attention-pulse {
  0%, 70%, 100% {
    box-shadow: 0 0 0 0 rgba(16, 185, 129, 0);
    border-color: rgba(16, 185, 129, 0.3);
    color: #10b981 !important;
    background: rgba(16, 185, 129, 0.08);
    transform: scale(1);
  }
  78%, 86% {
    box-shadow: 0 0 20px 4px rgba(16, 185, 129, 0.6), inset 0 0 10px 1px rgba(16, 185, 129, 0.3);
    border-color: #10b981;
    color: #ffffff !important;
    background: rgba(16, 185, 129, 0.22);
    transform: scale(1.05);
  }
  82% {
    box-shadow: 0 0 26px 6px rgba(16, 185, 129, 0.8), inset 0 0 14px 2px rgba(16, 185, 129, 0.4);
    border-color: #34d399;
    color: #ffffff !important;
    background: rgba(16, 185, 129, 0.3);
    transform: scale(1.08);
  }
}

.nav-contact-wrapper {
  position: relative;
  display: inline-flex;
  align-items: center;
}

.contact-navbar-popup {
  position: absolute;
  top: calc(100% + 16px);
  right: 0;
  width: 320px;
  background: #080a0f;
  border: 1px solid #10b981;
  border-radius: 8px;
  padding: 16px 18px;
  box-shadow: 0 16px 36px -8px rgba(0, 0, 0, 0.85), 0 0 24px -4px rgba(16, 185, 129, 0.3);
  z-index: 200;
  cursor: default;
}

.popup-arrow {
  position: absolute;
  top: -6px;
  right: 42px;
  width: 10px;
  height: 10px;
  background: #080a0f;
  border-left: 1px solid #10b981;
  border-top: 1px solid #10b981;
  transform: rotate(45deg);
}

.popup-status-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
}

.status-dot-pulse {
  width: 7px;
  height: 7px;
  background: #10b981;
  border-radius: 50%;
  box-shadow: 0 0 8px #10b981;
}

.status-label {
  font-family: monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #10b981;
  letter-spacing: 0.08em;
}

.popup-message {
  font-size: 0.86rem;
  color: #e2e8f0;
  line-height: 1.55;
  margin-bottom: 14px;
}

.popup-message strong {
  color: #ffffff;
  font-weight: 700;
}

.popup-actions {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

.btn-popup-cta {
  font-size: 0.78rem;
  font-weight: 700;
  color: #080a0f;
  background: #10b981;
  padding: 8px 14px;
  border-radius: 4px;
  text-decoration: none;
  transition: all 0.2s ease;
  flex: 1;
  text-align: center;
}

.btn-popup-cta:hover {
  background: #059669;
  transform: translateY(-1px);
}

.btn-popup-close {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.15);
  color: #94a3b8;
  width: 30px;
  height: 30px;
  border-radius: 4px;
  font-size: 1.15rem;
  line-height: 1;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.btn-popup-close:hover {
  color: #ffffff;
  border-color: #ef4444;
  background: rgba(239, 68, 68, 0.15);
}

.popup-fade-enter-active,
.popup-fade-leave-active {
  transition: all 0.35s cubic-bezier(0.16, 1, 0.3, 1);
}

.popup-fade-enter-from,
.popup-fade-leave-to {
  opacity: 0;
  transform: translateY(-12px) scale(0.95);
}

@media (max-width: 1080px) {
  .nav-menu {
    gap: 16px;
  }
  .nav-brand {
    padding-right: 14px;
  }
}

@media (max-width: 960px) {
  /* En móvil/tablet, ocultamos los enlaces 01 a 04 pero dejamos visible y accesible el botón 05. CONTACTO y su popup flotante */
  .nav-menu > a:not(.contact-glow-btn) {
    display: none;
  }
  .brand-tag {
    display: none;
  }
}

@media (max-width: 640px) {
  .nav-container {
    padding: 0 16px;
  }
  .brand-title {
    font-size: 0.82rem;
  }
  .contact-glow-btn {
    padding: 6px 12px !important;
    font-size: 0.78rem;
  }
  /* Ajustamos el popup en móvil para evitar desbordamiento horizontal */
  .contact-navbar-popup {
    right: -6px;
    width: calc(100vw - 32px);
    max-width: 310px;
    padding: 14px;
  }
  .popup-arrow {
    right: 32px;
  }
}

@media (max-width: 380px) {
  .brand-title {
    font-size: 0.76rem;
  }
}
</style>
