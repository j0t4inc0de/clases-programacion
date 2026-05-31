<script setup>
// No props needed since we link directly to LinkedIn
</script>

<template>
  <section id="sobre-mi" class="about-section">
    <div class="container about-container">
      <div class="about-text-content">
        <span class="section-tag">Trayectoria & Experiencia</span>
        <h2 class="section-title">¿Quién te enseñará?</h2>
        <p class="intro-p">
          Soy <strong>Juan Erices</strong>, Ingeniero en Informática y Desarrollador Frontend activo en la industria. Combino mi trabajo diario en proyectos tecnológicos reales con mi pasión por enseñar programación y Python a estudiantes principiantes de forma paciente, estructurada y muy práctica.
        </p>
        
        <div class="credentials-grid">
          <!-- Credential 1: Ingeniero & Analista -->
          <div class="credential-item">
            <div class="credential-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 14l9-5-9-5-9 5 9 5zm0 0l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14zm-4 6v-7.5l4-2.222" />
              </svg>
            </div>
            <div>
              <h4>Ingeniero en Informática & Analista Programador</h4>
              <p>Titulado por INACAP con formación sólida en bases de datos relacionales, algoritmos, aplicaciones web e ingeniería de software.</p>
            </div>
          </div>
          
          <!-- Credential 2: Desarrollador Frontend IoT -->
          <div class="credential-item">
            <div class="credential-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
              </svg>
            </div>
            <div>
              <h4>Desarrollador Frontend Activo</h4>
              <p>Experiencia en el desarrollo de plataformas IoT de monitoreo industrial en tiempo real mediante Vue.js 3 y consumo de APIs REST.</p>
            </div>
          </div>

          <!-- Credential 3: Cisco Python Certificado -->
          <div class="credential-item">
            <div class="credential-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
              </svg>
            </div>
            <div>
              <h4>Certificación Cisco PCAP en Python</h4>
              <p>Especialización validada en programación en Python, lógica de control, diagramación, modularización y buenas prácticas de desarrollo.</p>
            </div>
          </div>

          <!-- Credential 4: Ayudante & Sello Innovacion -->
          <div class="credential-item">
            <div class="credential-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.907c.961 0 1.36 1.246.588 1.81l-3.974 2.887a1 1 0 00-.364 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.364-1.118L2.49 11.1c-.773-.564-.374-1.81.588-1.81h4.907a1 1 0 00.95-.69l1.519-4.674z" />
              </svg>
            </div>
            <div>
              <h4>Sello de Innovación 2025 & Ex-Ayudante</h4>
              <p>Reconocido por proyectos académicos de impacto. Ex-ayudante de Bases de Datos Relacionales (SQL) y tutor independiente experimentado.</p>
            </div>
          </div>
        </div>

        <a 
          href="https://www.linkedin.com/in/juan-erices-fuentealba-628b4a27a" 
          target="_blank" 
          rel="noopener noreferrer" 
          class="linkedin-btn about-cta-anim"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="28"
            height="28"
            fill="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              d="M18.3362 18.339H15.6707V14.1622C15.6707 13.1662 15.6505 11.8845 14.2817 11.8845C12.892 11.8845 12.6797 12.9683 12.6797 14.0887V18.339H10.0142V9.75H12.5747V10.9207H12.6092C12.967 10.2457 13.837 9.53325 15.1367 9.53325C17.8375 9.53325 18.337 11.3108 18.337 13.6245V18.339H18.3362ZM7.00373 8.57475C6.14573 8.57475 5.45648 7.88025 5.45648 7.026C5.45648 6.1725 6.14648 5.47875 7.00373 5.47875C7.85873 5.47875 8.55173 6.1725 8.55173 7.026C8.55173 7.88025 7.85798 8.57475 7.00373 8.57475ZM8.34023 18.339H5.66723V9.75H8.34023V18.339ZM19.6697 3H4.32923C3.59498 3 3.00098 3.5805 3.00098 4.29675V19.7033C3.00098 20.4202 3.59498 21 4.32923 21H19.6675C20.401 21 21.001 20.4202 21.001 19.7033V4.29675C21.001 3.5805 20.401 3 19.6675 3H19.6697Z"
            ></path>
          </svg>
          <span>LinkedIn</span>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  background-color: var(--bg-secondary);
}

.about-container {
  display: block;
  max-width: 800px;
  margin: 0 auto;
}

.about-text-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.intro-p {
  font-size: 1.15rem;
  line-height: 1.7;
  color: var(--text-primary);
  margin-bottom: 30px;
}

.intro-p strong {
  color: var(--accent);
}

.credentials-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px 40px;
  margin-bottom: 48px;
  width: 100%;
  text-align: left;
}

.credential-item {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.credential-icon {
  background-color: var(--bg-primary);
  color: var(--accent);
  width: 50px;
  height: 50px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--border-color);
  flex-shrink: 0;
}

.credential-item h4 {
  font-size: 1.05rem;
  margin-bottom: 4px;
}

.credential-item p {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

.about-cta-anim {
  margin-top: 10px;
}

.linkedin-btn {
  background: transparent;
  position: relative;
  padding: 3px 40px;
  display: inline-flex;
  align-items: center;
  font-family: var(--font-heading);
  font-size: 17px;
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  border: 1px solid rgb(0, 119, 181);
  border-radius: 15px;
  outline: none;
  overflow: hidden;
  color: rgb(0, 119, 181);
  transition: color 0.3s 0.1s ease-out, border-color 0.3s ease;
  text-align: center;
  z-index: 10;
}

.linkedin-btn span {
  margin: 10px;
}

.linkedin-btn::before {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
  content: "";
  border-radius: 50%;
  display: block;
  width: 20em;
  height: 20em;
  left: -5em;
  text-align: center;
  transition: box-shadow 0.5s ease-out;
  z-index: -1;
}

.linkedin-btn:hover {
  color: #fff !important;
  border: 1px solid rgb(0, 119, 181);
}

.linkedin-btn:hover::before {
  box-shadow: inset 0 0 0 10em rgb(0, 119, 181);
}

@media (max-width: 992px) {
  .credentials-grid {
    grid-template-columns: 1fr;
    gap: 24px;
    margin-bottom: 36px;
  }
  .credential-item {
    text-align: left;
  }
}
</style>
