<script setup>
import HeaderSection from './components/HeaderSection.vue';
import HeroSection from './components/HeroSection.vue';
import AboutSection from './components/AboutSection.vue';
import TestimonialsSection from './components/TestimonialsSection.vue';
import BenefitsSection from './components/BenefitsSection.vue';
import FeaturesSection from './components/FeaturesSection.vue';
import FormSection from './components/FormSection.vue';
import AboutMentorSection from './components/AboutMentorSection.vue';
import LastCallSection from './components/LastCallSection.vue';
import FooterSection from './components/FooterSection.vue';
</script>

<template>
  <div class="font-sans text-dark">
    <HeaderSection />
    <HeroSection />
    <AboutSection />
    <TestimonialsSection />
    <BenefitsSection />
    <FeaturesSection />
    <FormSection />
    <AboutMentorSection />
    <LastCallSection />
    <FooterSection />
  </div>
</template>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {
  .container {
    @apply px-4 mx-auto max-w-7xl;
  }
  
  .section-title {
    @apply text-3xl md:text-4xl font-bold text-center mb-12;
  }
  
  .gradient-text {
    @apply bg-clip-text text-transparent bg-gradient-to-r from-primary to-accent;
  }
  
  .btn-primary {
    @apply bg-gradient-to-r from-primary to-accent text-white font-bold py-4 px-8 rounded-full shadow-lg hover:shadow-xl transition-all duration-300 uppercase tracking-wide text-center inline-block;
  }
}

html {
  scroll-behavior: smooth;
}

body {
  overflow-x: hidden;
}
</style>
