<script setup>
import { ref, onMounted } from 'vue'

const isDark = ref(true)

const toggleTheme = () => {
  isDark.value = !isDark.value
  updateTheme()
}

const updateTheme = () => {
  if (isDark.value) {
    document.documentElement.classList.remove('light-theme')
    localStorage.setItem('theme', 'dark')
  } else {
    document.documentElement.classList.add('light-theme')
    localStorage.setItem('theme', 'light')
  }
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme === 'light') {
    isDark.value = false
  } else {
    isDark.value = true
  }
  updateTheme()
})
</script>

<template>
  <button 
    @click="toggleTheme" 
    class="theme-toggle-btn" 
    :class="{ 'is-dark': isDark }"
    aria-label="Alternar tema de color"
  >
    <div class="icon-wrapper">
      <!-- Sun Icon -->
      <svg 
        class="sun-icon" 
        xmlns="http://www.w3.org/2000/svg" 
        viewBox="0 0 24 24" 
        fill="none" 
        stroke="currentColor" 
        stroke-width="2" 
        stroke-linecap="round" 
        stroke-linejoin="round"
      >
        <circle cx="12" cy="12" r="4"></circle>
        <path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M6.34 17.66l-1.41 1.41M19.07 4.93l-1.41 1.41"></path>
      </svg>
      <!-- Moon Icon -->
      <svg 
        class="moon-icon" 
        xmlns="http://www.w3.org/2000/svg" 
        viewBox="0 0 24 24" 
        fill="none" 
        stroke="currentColor" 
        stroke-width="2" 
        stroke-linecap="round" 
        stroke-linejoin="round"
      >
        <path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z"></path>
      </svg>
    </div>
  </button>
</template>

<style scoped>
.theme-toggle-btn {
  position: relative;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--bg-secondary);
  border: 1px solid var(--border-color);
  color: var(--text-primary);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275), 
              background-color 0.4s ease, 
              border-color 0.4s ease, 
              color 0.4s ease;
  overflow: hidden;
  flex-shrink: 0;
}

.theme-toggle-btn:hover {
  transform: scale(1.05);
  border-color: var(--accent);
  background-color: var(--bg-tertiary);
}

.theme-toggle-btn:active {
  transform: scale(0.95);
}

.icon-wrapper {
  position: relative;
  width: 18px;
  height: 18px;
}

.sun-icon, .moon-icon {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1), 
              opacity 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.is-dark .sun-icon {
  transform: rotate(90deg) scale(0);
  opacity: 0;
}

.is-dark .moon-icon {
  transform: rotate(0) scale(1);
  opacity: 1;
  color: var(--accent);
}

.is-dark:hover .moon-icon {
  color: var(--accent-green);
}

:not(.is-dark) .sun-icon {
  transform: rotate(0) scale(1);
  opacity: 1;
  color: var(--accent);
}

:not(.is-dark):hover .sun-icon {
  color: var(--accent-green);
}

:not(.is-dark) .moon-icon {
  transform: rotate(-90deg) scale(0);
  opacity: 0;
}
</style>
