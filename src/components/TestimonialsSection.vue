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
            <div class="bg-white/10 backdrop-blur-md rounded-xl p-6 h-full flex flex-col shadow-xl border border-accent/20">
              <div class="flex items-center mb-4">
                <div class="w-16 h-16 rounded-full overflow-hidden border-2 border-accent flex-shrink-0">
                  <img :src="testimonial.avatar" alt="Avatar" class="w-full h-full object-cover" />
                </div>
                <div class="ml-4">
                  <h4 class="font-bold text-lg">{{ testimonial.name }}</h4>
                  <p class="text-sm text-accent">{{ testimonial.profession }}</p>
                </div>
              </div>
              
              <div class="mb-4 text-accent">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 opacity-50" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M13 14.725c0-5.141 3.892-10.519 10-11.725l.984 2.126c-2.215.835-4.163 3.742-4.38 5.746 2.491.392 4.396 2.547 4.396 5.149 0 3.182-2.584 4.979-5.199 4.979-3.015 0-5.801-2.305-5.801-6.275zm-13 0c0-5.141 3.892-10.519 10-11.725l.984 2.126c-2.215.835-4.163 3.742-4.38 5.746 2.491.392 4.396 2.547 4.396 5.149 0 3.182-2.584 4.979-5.199 4.979-3.015 0-5.801-2.305-5.801-6.275z" />
                </svg>
              </div>
              
              <p class="text-white/90 mb-4 flex-grow">{{ testimonial.text }}</p>
              
              <div class="flex text-accent">
                <span v-for="star in 5" :key="star" class="mr-1">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118l-2.8-2.034c-.783-.57-.38-1.81.588-1.81h3.462a1 1 0 00.95-.69l1.07-3.292z" />
                  </svg>
                </span>
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
    avatar: 'https://randomuser.me/api/portraits/women/1.jpg',
    text: 'Participar do workshop do Dr. Matheus foi um divisor de águas na minha carreira. As técnicas ensinadas e a confiança que adquiri me permitiram triplicar meu faturamento com procedimentos estéticos.'
  },
  {
    name: 'Dr. Carlos Lima',
    profession: 'Cirurgião Plástico',
    avatar: 'https://randomuser.me/api/portraits/men/2.jpg',
    text: 'Mesmo já sendo especialista na área, o workshop me proporcionou novas perspectivas e técnicas que revolucionaram minha abordagem. Recomendo fortemente para quem quer se destacar no mercado.'
  },
  {
    name: 'Dra. Juliana Mendes',
    profession: 'Biomédica Esteta',
    avatar: 'https://randomuser.me/api/portraits/women/3.jpg',
    text: 'A metodologia hands-on faz toda a diferença! Poder praticar sob supervisão direta do Dr. Matheus elevou minha confiança e precisão nos procedimentos. Investimento que se pagou em menos de um mês.'
  },
  {
    name: 'Dr. Ricardo Alves',
    profession: 'Dermatologista',
    avatar: 'https://randomuser.me/api/portraits/men/4.jpg',
    text: 'O nível de detalhamento e atenção que o Dr. Matheus dedica a cada aluno é impressionante. Dominar a técnica de full face com essa precisão transformou minha prática clínica completamente.'
  },
  {
    name: 'Dra. Ana Paula Costa',
    profession: 'Farmacêutica Esteta',
    avatar: 'https://randomuser.me/api/portraits/women/5.jpg',
    text: 'Saí do workshop com a certeza de que posso realizar qualquer procedimento facial com segurança. A metodologia é fantástica e o suporte pós-evento faz toda a diferença!'
  }
]);
</script>

<style scoped>
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
</style> 