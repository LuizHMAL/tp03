<script setup lang="ts">
import { computed, ref } from 'vue';

type CarouselSlide = {
  title: string;
  content: string;
};

const props = withDefaults(
  defineProps<{
    slides?: CarouselSlide[];
  }>(),
  {
    slides: () => [
      { title: 'Slide 1', content: 'Primeiro conteúdo do carrossel.' },
      { title: 'Slide 2', content: 'Segundo conteúdo do carrossel.' },
      { title: 'Slide 3', content: 'Terceiro conteúdo do carrossel.' },
    ],
  }
);

const currentIndex = ref(0);

const totalSlides = computed(() => props.slides.length);

const trackStyle = computed(() => ({
  transform: `translateX(-${currentIndex.value * 100}%)`,
}));

const goToSlide = (index: number) => {
  if (index < 0 || index >= totalSlides.value) {
    return;
  }

  currentIndex.value = index;
};

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % totalSlides.value;
};

const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + totalSlides.value) % totalSlides.value;
};
</script>

<template>
  <section class="carousel" aria-label="Carrossel" @click="nextSlide">
    <div class="viewport">
      <div class="track" :style="trackStyle">
        <article v-for="(slide, index) in props.slides" :key="index" class="slide">
          <h3>{{ slide.title }}</h3>
          <p>{{ slide.content }}</p>
        </article>
      </div>
    </div>

    <div class="controls">
      <button type="button" class="control" @click.stop="prevSlide">Anterior</button>
      <button type="button" class="control" @click.stop="nextSlide">Próximo</button>
    </div>

    <div class="indicators">
      <button
        v-for="(_, index) in props.slides"
        :key="index"
        type="button"
        class="dot"
        :class="{ active: index === currentIndex }"
        @click.stop="goToSlide(index)"
        :aria-label="`Ir para slide ${index + 1}`"
      />
    </div>
  </section>
</template>

<style scoped>
.carousel {
  width: 100%;
  max-width: 42rem;
  margin: 0 auto;
}

.viewport {
  overflow: hidden;
  border: 1px solid #dcdcdc;
  border-radius: 0.75rem;
}

.track {
  display: flex;
  transition: transform 0.3s ease;
}

.slide {
  min-width: 100%;
  padding: 1.25rem;
  box-sizing: border-box;
  height: 20rem;

}

.slide h3 {
  margin: 0 0 0.5rem;
}

.slide p {
  margin: 0;
}

.controls {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  margin-top: 0.75rem;
}

.control {
  border: 1px solid #999;
  border-radius: 0.5rem;
  background: #fff;
  padding: 0.4rem 0.8rem;
  cursor: pointer;
}

.indicators {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  margin-top: 0.75rem;
}

.dot {
  width: 0.7rem;
  height: 0.7rem;
  border-radius: 50%;
  border: 1px solid #777;
  background: transparent;
  cursor: pointer;
}

.dot.active {
  background: #777;
}
.slide:hover {
   
   transition: 0.3s;
   cursor: pointer;
   transform: scale(1.02);
}
</style>