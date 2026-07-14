<script setup>
</script>

<template>
  <section class="about-view">
    <div class="container">
      <div class="glass-panel about-card">
        <h1 class="about-title">Hola Mundo</h1>
        <p class="about-subtitle">
          Esta es la ruta <code>/about</code> de la plataforma de clases particulares de programación de Juan Erices.
        </p>
        <div class="about-actions">
          <router-link to="/" class="btn btn-primary">
            ← Volver al inicio
          </router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-view {
  min-height: calc(100vh - 100px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 80px 20px;
  background-color: var(--bg-primary);
}

.about-card {
  max-width: 650px;
  margin: 0 auto;
  padding: 60px 40px;
  text-align: center;
  border: 1px solid var(--glass-border);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
}

.about-title {
  font-size: 3.5rem;
  font-weight: 800;
  margin-bottom: 24px;
  background: linear-gradient(135deg, var(--accent) 0%, #60a5fa 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.about-subtitle {
  font-size: 1.25rem;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 36px;
}

code {
  background-color: var(--bg-tertiary);
  padding: 4px 10px;
  border-radius: 6px;
  color: var(--accent);
  font-family: monospace;
  font-size: 1.1rem;
}

.about-actions {
  display: flex;
  justify-content: center;
}
</style>
