<template>
  <section class="py-16 bg-gradient-to-br from-dark to-secondary text-white" id="depoimentos">
    <div class="container mx-auto px-4 md:px-6 max-w-6xl">
      <h2 class="section-title">
        <span class="gradient-text">O que dizem os profissionais que já participaram</span>
      </h2>
      
      <div class="mt-12">
        <Swiper
          :modules="[Pagination, Autoplay]"
          :slides-per-view="1"
          :breakpoints="{
            '640': { slidesPerView: 1 },
            '768': { slidesPerView: 2 },
            '1024': { slidesPerView: 3 },
          }"
          :space-between="24"
          :pagination="{ clickable: true }"
          :autoplay="{ delay: 5000, disableOnInteraction: false }"
          class="testimonials-swiper"
        >
          <SwiperSlide v-for="(testimonial, index) in testimonials" :key="index">
            <div class="testimonial-card bg-white/10 backdrop-blur-md rounded-xl p-6 shadow-xl border border-accent/20">
              <!-- Header com Avatar e Info -->
              <div class="testimonial-header flex items-center gap-4 mb-6">
                <div class="w-12 h-12 rounded-full bg-accent/20 flex items-center justify-center flex-shrink-0">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
                  </svg>
                </div>
                <div class="min-w-0 flex-1">
                  <h4 class="font-bold text-lg text-white truncate">{{ testimonial.name }}</h4>
                  <p class="text-sm text-accent truncate">{{ testimonial.profession }}</p>
                </div>
              </div>

              <!-- Ícone de Aspas -->
              <div class="testimonial-quote mb-4 text-accent">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 opacity-50" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M13 14.725c0-5.141 3.892-10.519 10-11.725l.984 2.126c-2.215.835-4.163 3.742-4.38 5.746 2.491.392 4.396 2.547 4.396 5.149 0 3.182-2.584 4.979-5.199 4.979-3.015 0-5.801-2.305-5.801-6.275zm-13 0c0-5.141 3.892-10.519 10-11.725l.984 2.126c-2.215.835-4.163 3.742-4.38 5.746 2.491.392 4.396 2.547 4.396 5.149 0 3.182-2.584 4.979-5.199 4.979-3.015 0-5.801-2.305-5.801-6.275z" />
                </svg>
              </div>
              
              <!-- Conteúdo do Depoimento -->
              <div class="testimonial-content">
                <p class="text-white/90 text-sm leading-relaxed">{{ testimonial.text }}</p>
              </div>
              
              <!-- Estrelas (Footer) -->
              <div class="testimonial-footer mt-6 pt-4 border-t border-white/10">
                <div class="flex justify-center text-accent">
                  <span v-for="star in 5" :key="star" class="mr-1">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118l-2.8-2.034c-.783-.57-.38-1.81.588-1.81h3.462a1 1 0 00.95-.69l1.07-3.292z" />
                    </svg>
                  </span>
                </div>
              </div>
            </div>
          </SwiperSlide>
        </Swiper>
      </div>
      
      <div class="mt-16 text-center">
        <a href="#formulario" class="btn-primary">
          QUERO FAZER PARTE DESSA TRANSFORMAÇÃO
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Pagination, Autoplay } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/pagination';

const testimonials = ref([
  {
    name: 'Dra. Maria Santos',
    profession: 'Dentista',
    text: 'Eu pensava que sabia muita coisa e vi que não sabia absolutamente nada. No último dia do workshop, em que apliquei em um paciente de verdade, com o apoio de um profissional, virou uma chave de confiança na minha vida. Hoje eu faço procedimentos sem medo!'
  },
  {
    name: 'Dr. Carlos Lima',
    profession: 'Farmacêutico',
    text: 'Participar do workshop do Dr. Matheus foi um divisor de águas na minha carreira. Aprendi técnicas que não vi em nenhum outro lugar e me senti muito mais segura para realizar qualquer procedimento.'
  },
  {
    name: 'Dra. Juliana Mendes',
    profession: 'Dermatologista',
    text: 'Já fiz diversos cursos, mas ainda tinha muito receio de aplicar, principalmente nos lábios. Participar de um workshop com paciente modelo fez toda a diferença pra mim.'
  },
  {
    name: 'Dr. Ricardo Alves',
    profession: 'Cirurgião Plástico',
    text: 'Eu já me considerava um especialista, até conhecer o Dr. Matheus. Um pequeno detalhe que aprendi fez total diferença nos resultados dos meus pacientes.'
  },
  {
    name: 'Dra. Ana Paula Costa',
    profession: 'Dentista',
    text: 'Poder realizar um procedimento em pacientes com o acompanhamento de um professor é outra coisa. Essa experiência mudou minha vida.'
  }
]);
</script>

<style scoped>
/* Card padronizado com altura fixa */
.testimonial-card {
  height: 380px;
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.testimonial-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

/* Header fixo */
.testimonial-header {
  height: 64px;
  flex-shrink: 0;
}

/* Ícone de aspas fixo */
.testimonial-quote {
  height: 32px;
  flex-shrink: 0;
}

/* Conteúdo expansível */
.testimonial-content {
  flex: 1;
  display: flex;
  align-items: flex-start;
  overflow: hidden;
}

.testimonial-content p {
  display: -webkit-box;
  -webkit-line-clamp: 6;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  line-height: 1.6;
}

/* Footer fixo */
.testimonial-footer {
  height: 40px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
}

/* Estilizando os controles do Swiper */
:deep(.swiper-pagination-bullet) {
  background-color: #FFA149;
  opacity: 0.5;
}

:deep(.swiper-pagination-bullet-active) {
  background-color: #FF6B00;
  opacity: 1;
}

.testimonials-swiper {
  padding-bottom: 50px;
}

/* Garantir espaçamento consistente em diferentes telas */
@media (max-width: 768px) {
  .testimonial-card {
    height: 350px;
  }
  
  .testimonial-content p {
    -webkit-line-clamp: 5;
  }
}

@media (min-width: 1024px) {
  .testimonial-card {
    height: 400px;
  }
  
  .testimonial-content p {
    -webkit-line-clamp: 7;
  }
}
</style>