<script setup>
import { ref } from 'vue'
import ThemeToggle from './ThemeToggle.vue'

defineProps({
  whatsappLink: {
    type: String,
    required: true
  }
})

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
</script>

<template>
  <header class="main-header glass-panel">
    <div class="container header-container">
      <router-link to="/" class="logo">
        <span class="logo-code">&lt;</span>
        <span class="logo-name">Juan Erices</span>
        <span class="logo-code">/&gt;</span>
      </router-link>

      <!-- Desktop Nav -->
      <nav class="desktop-nav">
        <router-link to="/#aprender">¿Qué aprenderás?</router-link>
        <router-link to="/#sobre-mi">Sobre mí</router-link>
        <router-link to="/#planes">Planes</router-link>
        <router-link to="/about">Acerca de</router-link>
        <a :href="whatsappLink" target="_blank" rel="noopener noreferrer" class="btn-accent-anim nav-agendar-btn">
          <div class="circle c-1"></div>
          <div class="circle c-2"></div>
          <div class="circle c-3"></div>
          <div class="circle c-4"></div>
          <span class="btn-text">
            Agendar Cita
          </span>
        </a>
        <ThemeToggle />
      </nav>

      <!-- Mobile Actions (visible only on mobile) -->
      <div class="mobile-actions">
        <ThemeToggle />
        <button 
          class="mobile-menu-btn" 
          @click="toggleMobileMenu" 
          :class="{ 'is-active': isMobileMenuOpen }"
          aria-label="Menú de navegación"
        >
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </button>
      </div>
    </div>

    <!-- Mobile Drawer Menu -->
    <div class="mobile-nav" :class="{ 'is-open': isMobileMenuOpen }">
      <nav class="mobile-nav-links">
        <router-link to="/#aprender" @click="closeMobileMenu">¿Qué aprenderás?</router-link>
        <router-link to="/#sobre-mi" @click="closeMobileMenu">Sobre mí</router-link>
        <router-link to="/#planes" @click="closeMobileMenu">Planes</router-link>
        <router-link to="/about" @click="closeMobileMenu">Acerca de</router-link>
        <a 
          :href="whatsappLink" 
          target="_blank" 
          rel="noopener noreferrer"
          class="btn btn-whatsapp pulse-btn" 
          @click="closeMobileMenu"
        >
          Agendar por WhatsApp
        </a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.main-header {
  position: fixed;
  top: 16px;
  left: 50%;
  transform: translateX(-50%);
  width: calc(100% - 48px);
  max-width: 1200px;
  height: 70px;
  z-index: 90;
  border-radius: 20px;
  transition: all 0.3s ease;
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}

.logo {
  display: flex;
  align-items: center;
  gap: 4px;
  font-family: var(--font-heading);
  font-weight: 800;
  font-size: 1.3rem;
  letter-spacing: -0.02em;
}

.logo-code {
  color: var(--accent);
  font-weight: 600;
}

.logo-name {
  color: var(--text-primary);
}

.desktop-nav {
  display: flex;
  align-items: center;
  gap: 32px;
}

.desktop-nav a {
  font-size: 0.95rem;
  font-weight: 500;
  color: var(--text-secondary);
  position: relative;
  padding: 6px 0;
}

.desktop-nav a:not(.btn):hover {
  color: var(--text-primary);
}

.desktop-nav a:not(.btn)::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--accent);
  transition: width 0.3s ease;
}

.desktop-nav a:not(.btn):hover::after {
  width: 100%;
}

.nav-agendar-btn {
  padding-left: 42px !important;
  padding-right: 42px !important;
  min-width: 185px !important;
}

/* Mobile Actions Wrapper */
.mobile-actions {
  display: none;
}

/* Mobile Menu Button */
.mobile-menu-btn {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 26px;
  height: 20px;
  background: transparent;
  border: none;
  cursor: pointer;
  z-index: 101;
}

.mobile-menu-btn .bar {
  width: 100%;
  height: 2px;
  background-color: var(--text-primary);
  transition: all 0.3s ease;
  border-radius: 2px;
}

.mobile-menu-btn.is-active .bar:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.mobile-menu-btn.is-active .bar:nth-child(2) {
  opacity: 0;
}

.mobile-menu-btn.is-active .bar:nth-child(3) {
  transform: translateY(-9px) rotate(-45deg);
}

/* Mobile Nav Drawer */
.mobile-nav {
  position: fixed;
  top: 96px;
  left: 0;
  width: 100%;
  background: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: 20px;
  padding: 24px;
  box-shadow: var(--shadow);
  transform: translateY(-20px);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s ease;
  z-index: 89;
}

.mobile-nav.is-open {
  transform: translateY(0);
  opacity: 1;
  pointer-events: auto;
}

.mobile-nav-links {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
}

.mobile-nav-links a:not(.btn) {
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--text-primary);
  width: 100%;
  text-align: center;
  padding: 8px 0;
}

.mobile-nav-links .btn {
  width: 100%;
  margin-top: 10px;
}

@media (max-width: 768px) {
  .main-header {
    top: 12px;
    width: calc(100% - 24px);
    height: 60px;
  }
  .desktop-nav {
    display: none;
  }
  .mobile-actions {
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .mobile-menu-btn {
    display: flex;
  }
}
</style>
