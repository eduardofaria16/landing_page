<template>
  <section class="py-16 bg-white" id="beneficios">
    <div class="container mx-auto px-4 md:px-6 max-w-6xl">
      <h2 class="section-title">
        <span class="gradient-text">Como você vai sair desse evento:</span>
      </h2>
      
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div 
          v-for="(benefit, index) in benefits" 
          :key="index"
          class="benefit-card bg-white rounded-2xl shadow-lg overflow-hidden transform transition-all duration-500 hover:scale-105"
          :class="{'animate-fade-in': isVisible}"
          :style="{transitionDelay: `${index * 150}ms`}"
          ref="benefitCards"
        >
          <div class="h-2 bg-gradient-to-r from-primary to-accent"></div>
          <div class="p-8">
            <div class="mb-5 text-4xl text-accent">
              <component :is="benefit.icon"></component>
            </div>
            <h3 class="text-xl font-bold mb-3 text-gray-800">{{ benefit.title }}</h3>
            <p class="text-gray-700">{{ benefit.description }}</p>
          </div>
        </div>
      </div>
      
      <div class="mt-16 text-center">
        <a href="#formulario" class="btn-primary">
          QUERO TRANSFORMAR MINHA CARREIRA
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const benefitCards = ref([]);
const isVisible = ref(false);
const sectionRef = ref(null);

const benefits = [
  {
    icon: 'IconAuthority',
    title: 'Como uma autoridade no mercado',
    description: 'Você será reconhecido como um especialista em harmonização facial, com técnicas exclusivas e resultados superiores que destacarão seu trabalho.'
  },
  {
    icon: 'IconConfidence',
    title: 'Confiante para realizar qualquer procedimento facial',
    description: 'A prática intensiva com supervisão especializada eliminará suas inseguranças, permitindo que você enfrente até os casos mais desafiadores.'
  },
  {
    icon: 'IconValue',
    title: 'Confiante para se valorizar e aumentar seus preços',
    description: 'Com novas habilidades e resultados diferenciados, você terá a segurança para cobrar o que seu trabalho realmente vale no mercado.'
  }
];

// Componentes de ícones
const IconAuthority = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-12 h-12">
      <path stroke-linecap="round" stroke-linejoin="round" d="M3 13.125C3 12.504 3.504 12 4.125 12h2.25c.621 0 1.125.504 1.125 1.125v6.75C7.5 20.496 6.996 21 6.375 21h-2.25A1.125 1.125 0 013 19.875v-6.75zM9.75 8.625c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125v11.25c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V8.625zM16.5 4.125c0-.621.504-1.125 1.125-1.125h2.25C20.496 3 21 3.504 21 4.125v15.75c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V4.125z" />
    </svg>
  `
};

const IconConfidence = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-12 h-12">
      <path stroke-linecap="round" stroke-linejoin="round" d="M15.59 14.37a6 6 0 01-5.84 7.38v-4.8m5.84-2.58a14.98 14.98 0 006.16-12.12A14.98 14.98 0 009.631 8.41m5.96 5.96a14.926 14.926 0 01-5.841 2.58m-.119-8.54a6 6 0 00-7.381 5.84h4.8m2.581-5.84a14.927 14.927 0 00-2.58 5.84m2.699 2.7c-.103.021-.207.041-.311.06a15.09 15.09 0 01-2.448-2.448 14.9 14.9 0 01.06-.312m-2.24 2.39a4.493 4.493 0 00-1.757 4.306 4.493 4.493 0 004.306-1.758M16.5 9a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z" />
    </svg>
  `
};

const IconValue = {
  template: `
    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-12 h-12">
      <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m-3-2.818l.879.659c1.171.879 3.07.879 4.242 0 1.172-.879 1.172-2.303 0-3.182C13.536 12.219 12.768 12 12 12c-.725 0-1.45-.22-2.003-.659-1.106-.879-1.106-2.303 0-3.182s2.9-.879 4.006 0l.415.33M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  `
};

onMounted(() => {
  // Configurar IntersectionObserver para animar os cards quando visíveis
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        isVisible.value = true;
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.3 });
  
  const sectionElement = document.getElementById('beneficios');
  if (sectionElement) {
    observer.observe(sectionElement);
  }
  
  return () => {
    if (sectionElement) {
      observer.unobserve(sectionElement);
    }
  };
});
</script>

<style scoped>
.benefit-card {
  opacity: 0;
  transform: translateY(20px);
}

.benefit-card.animate-fade-in {
  opacity: 1;
  transform: translateY(0);
}
</style>
