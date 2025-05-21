<template>
  <header class="fixed top-0 left-0 w-full bg-dark/90 backdrop-blur-md z-50 py-2">
    <div class="container flex justify-between items-center">

      <div class="ticker-wrapper overflow-hidden w-full max-w-lg mx-auto">
        <div class="ticker-move">
          <div class="ticker-content text-white font-medium flex whitespace-nowrap">
           <template v-for="n in 2" :key="n">
            <span class="ticker-item">Workshop Hands On</span>
            <span class="ticker-separator">✦</span>
            <span class="ticker-item">{{ formattedDate }}</span>
            <span class="ticker-separator">✦</span>
            <span class="ticker-item">Restam {{ remainingSlots }} vagas</span>
            <span class="ticker-separator">✦</span>
            <span class="ticker-item">Últimas chamadas</span>
            <span class="ticker-separator">✦</span>
            </template>
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


const eventDate = new Date(); // Exemplo: 15 de julho de 2024

// Número de vagas restantes
const remainingSlots = ref(2);

// Formatar a data
const formattedDate = computed(() => {
  const options = { day: 'numeric', month: 'numeric' };
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

.ticker-content {
  display: inline-flex;
}

.ticker-item {
  display: inline-block;
  color: #FFA149;
  font-weight: 700;
}

.ticker-separator {
  display: inline-block;
  margin: 0 0.5rem;
}

@keyframes ticker {
  0% {
    transform: translateX(0%);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style> 