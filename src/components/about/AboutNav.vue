<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 40
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
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
        <a href="#contacto" class="nav-link contact-glow-btn"><span class="link-num">05.</span> CONTACTO</a>
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

@media (max-width: 1080px) {
  .nav-menu {
    gap: 20px;
  }
  .nav-brand {
    padding-right: 20px;
  }
}

@media (max-width: 960px) {
  .nav-menu {
    display: none;
  }
  .brand-tag {
    display: none;
  }
}

@media (max-width: 640px) {
  .nav-container {
    padding: 0 18px;
  }
  .brand-title {
    font-size: 0.85rem;
  }
}
</style>
