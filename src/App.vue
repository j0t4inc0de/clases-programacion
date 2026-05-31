<script setup>
import { ref, computed } from 'vue'
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
import WhatYouLearn from './components/WhatYouLearn.vue'
import ForWhoSection from './components/ForWhoSection.vue'
import PlansSection from './components/PlansSection.vue'
import TrustSection from './components/TrustSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

// ==========================================
// CONFIGURACIÓN CENTRALIZADA DE JUAN ERICES
// ==========================================

// Cambiar por el número de WhatsApp real (Ej: código de país + número, sin el "+")
// Ejemplo para Chile: 56912345678
const phoneNumber = ref('56948991554')

// Mensaje predeterminado que recibirá Juan al iniciar el chat
const messageText = ref('Hola Juan, me gustaría consultar por tus clases particulares de programación.')

// Correo de contacto académico/profesional
const contactEmail = ref('jericesb5@gmail.com')

// Disponibilidad horaria aproximada
const currentAvailability = ref('Lunes a Viernes: 15:00 - 21:00 | Sábados: 10:00 - 17:00')

// Enlace de WhatsApp generado dinámicamente
const whatsappLink = computed(() => {
  const encodedText = encodeURIComponent(messageText.value)
  return `https://wa.me/${phoneNumber.value}?text=${encodedText}`
})
</script>

<template>
  <Header :whatsapp-link="whatsappLink" />
  
  <main>
    <HeroSection :whatsapp-link="whatsappLink" />
    
    <WhatYouLearn />
    
    <ForWhoSection />
    
    <AboutSection />
    
    <PlansSection :phone-number="phoneNumber" />
    
    <TrustSection />
    
    <ContactSection 
      :whatsapp-link="whatsappLink"
      :email="contactEmail"
      :availability="currentAvailability"
    />
  </main>
</template>

<style>
/* Estilos globales rápidos */
main {
  min-height: 100vh;
}
</style>
