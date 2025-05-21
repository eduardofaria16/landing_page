<template>
  <section class="min-h-screen pt-14  md:pt-28 pb-16 relative bg-gradient-to-br from-dark to-secondary overflow-hidden" id="doctor-image">
    <div class="absolute inset-0 opacity-15">
      <div class="absolute inset-0 bg-gradient-to-b from-transparent to-dark"></div>
    </div>
    
    <div class="container relative z-10 flex flex-col md:flex-row items-center justify-between gap-8">
      <div class="relative">
          <div class="rounded-2xl overflow-hidden border-2 border-accent relative z-10">
            <img src="/images/Doctor.png" alt="Dr. Matheus" class="w-full h-auto" />
          </div>
          <div class="absolute inset-0 bg-gradient-to-r from-primary to-accent rounded-2xl transform rotate-3 -z-0"></div>
        </div>
      
      <div class="w-full md:w-7/12 text-white">
        <div class="animate-fade-in">
          <p class="text-md text-center md:text-xl text-accent mb-3 font-medium">De 14 a 20 de julho | Presencial | Aracaju/SE</p>
          <h1 class="text-center text-3xl md:text-6xl lg:text-7xl font-bold mb-4">
            <span class="gradient-text">2 dias de Workshop</span>
          </h1>
          <h2 class="text-center text-3xl md:text-4xl font-bold mb-6">HARMONIZAÇÃO FACIAL</h2>
          
          <div class="space-y-4 mb-8">
            <div class="bg-dark/40 backdrop-blur p-4 rounded-lg border border-accent/20" id="workshop-description">
              <p class="text-lg md:text-xl">2 dias de workshop para dominar as técnicas mais avançadas de harmonização facial e transformar sua carreira profissional</p>
            </div>
          </div>
          <div class="flex justify-center">
            <a href="#formulario" class="btn-primary">
              QUERO PARTICIPAR
            </a>
          </div>
        </div>
      </div>
    </div>
    
    <div class="absolute bottom-0 left-0 w-full h-32 bg-gradient-to-t from-dark to-transparent"></div>
  </section>
</template>

<script setup>
import { computed } from 'vue';

// Data do workshop (adicione a data real aqui)
const eventDate = new Date('2024-07-15'); // Exemplo: 15 de julho de 2024

// Formatar a data
const formattedDate = computed(() => {
  const options = { day: 'numeric', month: 'long', year: 'numeric' };
  return eventDate.toLocaleDateString('pt-BR', options);
});
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 1s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
</style> 