<script setup lang="ts">

import { ref, onMounted } from 'vue'

const stars = ref<
  { id: number; x: number; y: number; size: number; delay: number }[]
>([])

onMounted(() => {
  for (let i = 0; i < 50; i++) {
    stars.value.push({
      id: i,
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: Math.random() * 3 + 1,
      delay: Math.random() * 5
    })
  }
})
const skillGroups = [
  {
    title: 'Développement',
    skills: [
      'Python',
      'PHP',
      'JavaScript',
      'Java',
      'C++',
      'Angular',
      'Laravel',
      'HTML / CSS',
      'Architecture MVC',
    ]
  },
  {
    title: 'Algorithmique',
    skills: [
      'Structures de données',
      'Algorithmes de tri',
      'Divide & Conquer',
      'Backtracking',
      'Programmation dynamique'
    ]
  },
  {
    title: 'Data',
    skills: [
      'MySQL',
      'Pandas',
      'Scikit-learn',
      'Power BI / DAX'
    ]
  },
  {
    title: 'Outils & Méthodes',
    skills: [
      'Git',
      'Gestion de projet',
      'Méthodes Agile',
      'Travail en équipe'
    ]
  },
  {
    title: 'Langues',
    skills: [
      'Français — langue maternelle',
      'Anglais — B2 · TOEIC 910',
      'Allemand — C1',
      'Espagnol — A2'
    ]
  }
]
</script>

<template>
  <section id="skills" class="skills">
    <span
      v-for="star in stars"
      :key="star.id"
      class="skills-star"
      :style="{
        left: `${star.x}%`,
        top: `${star.y}%`,
        width: `${star.size}px`,
        height: `${star.size}px`,
        animationDelay: `${star.delay}s`
    }"
    ></span>

    <div class="skills-content">

      <div class="skills-title">
        <span>04</span>
        <h2>Compétences</h2>
      </div>

      <div class="skills-grid">

        <div
          v-for="group in skillGroups"
          :key="group.title"
          class="skill-group"
        >

          <h3>{{ group.title }}</h3>

          <div class="skill-list">
            <span
              v-for="skill in group.skills"
              :key="skill"
              class="skill"
            >
              {{ skill }}
            </span>
          </div>

        </div>

      </div>

    </div>

  </section>
</template>
