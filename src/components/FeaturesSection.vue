<template>
  <section class="py-16 bg-gradient-to-br from-dark to-secondary text-white" id="caracteristicas">
    <div class="container mx-auto px-4 md:px-6 max-w-6xl">
      <h2 class="section-title">
        <span class="gradient-text">Tudo o que você vai receber ao se inscrever:</span>
      </h2>
      
      <div class="mt-12 grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="bg-white/5 backdrop-blur-sm rounded-xl p-6 border border-accent/20">
          <ul class="space-y-6">
            <li v-for="(feature, index) in features" :key="index" class="flex">
              <div class="flex-shrink-0 mt-1 text-accent">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </div>
              <div class="ml-4">
                <h3 class="text-xl font-semibold text-accent mb-2">{{ feature.title }}</h3>
                <p class="text-white/80">{{ feature.description }}</p>
              </div>
            </li>
          </ul>
        </div>
        
        <div class="bg-gradient-to-br from-primary/20 to-accent/20 rounded-xl p-6 border border-accent/30 flex flex-col">
          <div class="bg-gradient-to-r from-primary to-accent text-white font-bold py-2 px-4 rounded-full text-center w-auto self-start mb-6">
            BÔNUS EXCLUSIVO
          </div>
          
          <div class="flex-grow flex flex-col items-center justify-center text-center p-6">
            <div class="w-24 h-24 rounded-full bg-accent/20 flex items-center justify-center mb-6">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 text-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
              </svg>
            </div>
            
            <h3 class="text-2xl font-bold text-accent mb-4">30 DIAS DE ACOMPANHAMENTO</h3>
            <p class="text-white/90 text-lg mb-6">
              Tenha acesso direto ao Dr. Matheus por 30 dias após o workshop para tirar dúvidas, compartilhar casos e receber orientações personalizadas para acelerar sua evolução.
            </p>
            
            <div class="text-accent font-bold">
              <p class="mt-2">GRÁTIS PARA PARTICIPANTES DO WORKSHOP</p>
            </div>
          </div>
        </div>
      </div>
      
      <div class="mt-16 text-center">
        <a href="#formulario" class="btn-primary">
          QUERO GARANTIR MINHA VAGA
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const features = ref([
  {
    title: 'Materiais exclusivos',
    description: 'Receba todos os materiais necessários para aproveitar ao máximo o conteúdo prático, incluindo apostilas detalhadas e guias de procedimentos.'
  },
  {
    title: 'Certificação reconhecida',
    description: 'Valide sua expertise com um certificado que agrega valor real ao seu currículo.'
  },
  {
    title: 'Equipamentos e produtos de alta qualidade',
    description: 'Acesso completo a tudo o que você precisa para realizar os procedimentos durante o workshop.'
  },
  {
    title: 'Networking com profissionais de alto nível',
    description: 'Conecte-se com colegas ambiciosos e crie oportunidades que podem mudar sua trajetória.'
  }
]);
</script> 