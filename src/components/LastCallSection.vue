<template>
  <section class="py-16 bg-white" id="ultima-chamada">
    <div class="container mx-auto px-4 md:px-6 max-w-6xl">
      <div class="bg-gradient-to-br from-primary/20 to-accent/20 rounded-2xl p-8 md:p-12 border border-primary/30 relative overflow-hidden">
        <div class="absolute top-0 right-0 w-64 h-64 bg-gradient-to-br from-primary to-accent rounded-full opacity-20 transform translate-x-1/3 -translate-y-1/3"></div>
        
        <h2 class="text-2xl md:text-3xl lg:text-4xl font-bold mb-6 relative z-10">
          <span class="gradient-text">Último aviso!</span>
        </h2>
        
        <p class="text-gray-700 text-lg md:text-xl mb-6 max-w-3xl relative z-10">
          O workshop é um evento fechado para quem realmente quer se tornar um profissional de alto nível, com acompanhamento de perto e prática em pacientes reais, por isso são <strong class="text-primary">apenas 5 vagas</strong>, sem possibilidade de mais aberturas.
        </p>
        
        <p class="text-gray-700 text-lg md:text-xl mb-8 max-w-3xl relative z-10">
          Se você está comprometido com a sua evolução profissional e quer dominar as técnicas mais avançadas de harmonização facial com um dos maiores especialistas do Brasil, essa é a sua oportunidade.
        </p>
        
        <div class="space-y-6 md:space-y-0 md:flex md:items-center md:space-x-6 relative z-10">
          <a href="#formulario" class="btn-primary block md:inline-block text-center">
            QUERO GARANTIR MINHA VAGA AGORA
          </a>
          
          <div class="flex items-center justify-center md:justify-start">
            <div class="text-primary mr-3">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <p class="font-medium text-gray-700">
              Restam apenas <span class="text-primary font-bold">{{ remainingSlots }} vagas!</span>
            </p>
          </div>
        </div>
      </div>
      
      <div class="mt-16 text-center">
        <div class="inline-block bg-gradient-to-r from-primary to-accent p-1 rounded-xl">
          <div class="bg-white px-6 py-3 rounded-lg">
            <p class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-accent font-bold">
              Data do Workshop: {{ formattedDate }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';

// Data do workshop (adicione a data real aqui)
const eventDate = new Date('2025-07-27'); // Exemplo: 15 de julho de 2024

// Número de vagas restantes
const remainingSlots = ref(2);

// Formatar a data
const formattedDate = computed(() => {
  const options = { day: 'numeric', month: 'long', year: 'numeric' };
  return eventDate.toLocaleDateString('pt-BR', options);
});
</script> 