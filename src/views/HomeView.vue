<script setup>
import HeroSection from '../components/HeroSection.vue'
import WhatYouLearn from '../components/WhatYouLearn.vue'
import ForWhoSection from '../components/ForWhoSection.vue'
import AboutSection from '../components/AboutSection.vue'
import PlansSection from '../components/PlansSection.vue'
import TrustSection from '../components/TrustSection.vue'
import ContactSection from '../components/ContactSection.vue'

defineProps({
  whatsappLink: String,
  phoneNumber: String,
  contactEmail: String,
  currentAvailability: String
})
</script>

<template>
  <div class="home-view">
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
  </div>
</template>
