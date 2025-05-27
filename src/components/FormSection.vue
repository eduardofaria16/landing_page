<template>
  <section class="py-16 bg-white" id="formulario">
    <div class="container mx-auto px-4 md:px-6 max-w-6xl">
      <h2 class="section-title">
        <span class="gradient-text">Garanta sua vaga no Workshop Hands On</span>
      </h2>
      
      <div class="mt-10 grid grid-cols-1 md:grid-cols-2 gap-12">
        <div class="bg-gradient-to-br from-primary/10 to-accent/10 p-6 md:p-8 rounded-2xl border border-primary/20">
          <h3 class="text-2xl font-bold mb-4 text-gray-800">Vagas limitadas!</h3>
          <p class="text-gray-700 mb-6">
            Para garantir a qualidade do aprendizado e a atenção individual, o workshop tem vagas extremamente limitadas, 
            <strong class="text-primary">apenas {{ remainingSlots }} vagas!</strong>
          </p>
          
          <div class="space-y-4 mb-8">
            <div class="flex items-center">
              <div class="text-accent mr-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                </svg>
              </div>
              <div>
                <p class="font-medium text-gray-800">Data do Workshop</p>
                <p class="text-gray-600">{{ formattedDate }}</p>
              </div>
            </div>
            
            <div class="flex items-center">
              <div class="text-accent mr-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
              </div>
              <div>
                <p class="font-medium text-gray-800">Local</p>
                <p class="text-gray-600">Aracaju -SE (Endereço será informado após confirmação)</p>
              </div>
            </div>
            
            <div class="flex items-center">
              <div class="text-accent mr-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
              </div>
              <div>
                <p class="font-medium text-gray-800">Duração</p>
                <p class="text-gray-600">2 dias de imersão total (16 horas)</p>
              </div>
            </div>
            
          </div>
        </div>
        
        <div>
          <form @submit.prevent="submitForm" class="space-y-6">
            <div>
              <label for="name" class="block text-sm font-medium text-gray-700 mb-1">Nome completo</label>
              <input 
                type="text" 
                id="name" 
                v-model="form.name" 
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary"
                placeholder="Digite seu nome completo"
              />
            </div>
            
            <div>
              <label for="email" class="block text-sm font-medium text-gray-700 mb-1">E-mail</label>
              <input 
                type="email" 
                id="email" 
                v-model="form.email" 
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary"
                placeholder="exemplo@email.com"
              />
            </div>
            
            <div>
              <label for="phone" class="block text-sm font-medium text-gray-700 mb-1">Telefone (WhatsApp)</label>
              <input 
                type="tel" 
                id="phone" 
                v-model="form.phone" 
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary"
                placeholder="(00) 00000-0000"
              />
            </div>
            
            <div>
              <label for="profession" class="block text-sm font-medium text-gray-700 mb-1">Profissão</label>
              <select 
                id="profession" 
                v-model="form.profession" 
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary"
              >
                <option value="" disabled selected>Selecione sua profissão</option>
                <option value="dentista">Dentista</option>
                <option value="medico">Médico(a)</option>
                <option value="farmaceutico">Farmacêutico(a)</option>
                <option value="fisioterapeuta">Fisioterapeuta</option>
                <option value="biomedico">Biomédico(a)</option>
                <option value="outro">Outro</option>
              </select>
            </div>
            
            <div>
              <label for="message" class="block text-sm font-medium text-gray-700 mb-1">Mensagem (opcional)</label>
              <textarea 
                id="message" 
                v-model="form.message" 
                rows="3"
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary"
                placeholder="Conte-nos o que você espera do workshop..."
              ></textarea>
            </div>
            
            <button 
              type="submit" 
              class="w-full btn-primary"
              :disabled="isSubmitting"
            >
              {{ isSubmitting ? 'ENVIANDO...' : 'GARANTIR MINHA VAGA' }}
            </button>
            
            <p class="text-center text-sm text-gray-500">
              Ao enviar, você concorda com nossos termos de uso e política de privacidade.
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';

// Data do workshop
const eventDate = new Date('2025-07-27'); // Exemplo: 15 de julho de 2024

// Número de vagas restantes
const remainingSlots = ref(5);

// Formatar a data
const formattedDate = computed(() => {
  const options = { day: 'numeric', month: 'long', year: 'numeric' };
  return eventDate.toLocaleDateString('pt-BR', options);
});

// Formulário
const form = ref({
  name: '',
  email: '',
  phone: '',
  profession: '',
  message: ''
});

const isSubmitting = ref(false);

// Enviar formulário
const submitForm = async () => {
  isSubmitting.value = true;

  try {
    await fetch("https://getform.io/f/bxowdmva", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(form.value)
    });

    alert("Inscrição realizada com sucesso!");
    form.value = {
      name: '',
      email: '',
      phone: '',
      profession: '',
      message: ''
    };
  } catch (error) {
    alert("Erro ao enviar o formulário. Tente novamente.");
    console.error(error);
  } finally {
    isSubmitting.value = false;
  }
};

</script> 