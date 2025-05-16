<template>
  <header class="fixed top-0 left-0 w-full bg-dark/90 backdrop-blur-md z-50 py-3">
    <div class="container flex justify-between items-center">
      <div class="text-white font-bold text-xl">
        <span class="gradient-text">Workshop Hands On</span>
      </div>
      
      <div class="ticker-wrapper overflow-hidden w-full max-w-lg mx-auto">
        <div class="ticker-move">
          <div class="text-white font-medium flex whitespace-nowrap">
            <span class="ticker-item">
              {{ formattedDate }} – Restam apenas {{ remainingSlots }} vagas!
            </span>
          </div>
        </div>
      </div>
      
      <a href="#formulario" class="hidden md:block text-white border border-primary hover:bg-primary/20 px-4 py-2 rounded-full transition-all">
        Inscrever-se
      </a>
    </div>
  </header>
</template>

<script setup>
import { ref, computed } from 'vue';

// Data do workshop (adicione a data real aqui)
const eventDate = new Date('2024-07-15'); // Exemplo: 15 de julho de 2024

// Número de vagas restantes
const remainingSlots = ref(2);

// Formatar a data
const formattedDate = computed(() => {
  const options = { day: 'numeric', month: 'long', year: 'numeric' };
  return eventDate.toLocaleDateString('pt-BR', options);
});
</script>

<style scoped>
.ticker-wrapper {
  position: relative;
  overflow: hidden;
}

.ticker-move {
  display: inline-block;
  white-space: nowrap;
  animation: ticker 20s linear infinite;
}

.ticker-item {
  display: inline-block;
  padding: 0 2rem;
  color: #FFA149;
  font-weight: 700;
}

@keyframes ticker {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}
</style> 