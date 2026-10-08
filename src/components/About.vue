<script setup lang="ts">
import { ref, onMounted } from 'vue'

const stars = ref<
  { id: number; x: number; y: number; size: number; delay: number }[]
>([])

onMounted(() => {
  for (let i = 0; i < 45; i++) {
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
  <section id="about" class="about">

    <!-- Ciel étoilé -->
    <div class="about-stars">
      <span
        v-for="star in stars"
        :key="star.id"
        class="about-star"
        :style="{
          left: `${star.x}%`,
          top: `${star.y}%`,
          width: `${star.size}px`,
          height: `${star.size}px`,
          animationDelay: `${star.delay}s`
        }"
      ></span>
    </div>

    <div class="about-content">

      <div class="about-title">
        <span>01</span>
        <h2>À propos</h2>
      </div>

      <div class="about-text">
        <p>
          Actuellement en dernière année d'école d'ingénieur à
          l'IMT Nord Europe, je me spécialise en ingénierie numérique,
          avec un intérêt particulier pour le développement informatique,
          l'algorithmique et la science des données.
        </p>

        <p>
          Au cours de mes expériences, j'ai travaillé sur des projets
          mêlant développement web, analyse de données et conception
          d'outils numériques.
        </p>

        <p>
          Je recherche actuellement un stage de fin d'études de 6 mois
          à partir de mars 2027, avec une préférence pour le développement
          logiciel et les projets nécessitant une forte réflexion algorithmique.
        </p>
        <p>
          Je suis également passionné de football, de jeux vidéo et de musique. Je pratique le football depuis mon plus jeune âge, et ce sport fait aujourd’hui partie intégrante de mon identité.
        </p>
      </div>

    </div>

  </section>
</template>