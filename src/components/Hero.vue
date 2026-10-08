<script setup lang="ts">
import { ref, onMounted } from 'vue'

const stars = ref<
  { id: number; x: number; y: number; size: number; delay: number }[]
>([])

onMounted(() => {
  for (let i = 0; i < 70; i++) {
    stars.value.push({
      id: i,
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: Math.random() * 3 + 1,
      delay: Math.random() * 5
    })
  }
})
</script>

<template>
  <section id="home" class="hero">

    <div class="stars">
      <span
        v-for="star in stars"
        :key="star.id"
        class="star"
        :style="{
          left: `${star.x}%`,
          top: `${star.y}%`,
          width: `${star.size}px`,
          height: `${star.size}px`,
          animationDelay: `${star.delay}s`
        }"
      ></span>
    </div>

    <div class="hero-content">

      <div class="hero-block hero-left">
        <p>
          Bonjour, je suis Samy Isik ! Étudiant à l’IMT Nord Europe, je suis spécialisé en développement informatique et en science des données.
        </p>
      </div>

      <div class="hero-block hero-right">
        <p>
          Je recherche un stage de fin d’études de 6 mois à partir de mars 2027 afin d’approfondir mes compétences dans ces domaines.
        </p>
      </div>

      <div class="hero-block hero-left">
        <p>
          
        </p>
      </div>

      <div class="hero-buttons">
        <a href="#projects">Mes projets</a>
        <a href="/CV_ISIK Samy_2027_DI.pdf" target="_blank" rel="noopener noreferrer">
          Mon CV
        </a>
      </div>

    </div>

  </section>
</template>