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
const projects = [
  {
    number: '01',
    title: 'Mahjong Riichi',
    category: 'Développement logiciel · Jeu vidéo',
    description:
      "Développement d'un jeu de Mahjong Riichi avec implémentation des règles et de la logique du jeu. Conception d'une base de données et structuration du projet selon le modèle MVC.",
    technologies: ['Typescript', 'MVC', 'Base de données', 'Git'],
    image: '/projects/mahjong.jpg',
    color: '#b56cff',

  },
  {
    number: '02',
    title: 'Site Web — Association Adolice',
    category: 'Développement Web',
    description:
      "Développement d'un site web pour l'association Adolice en Laravel et PHP, selon une architecture MVC. Travail en équipe avec répartition des tâches via Trello et gestion du code avec GitHub.",
    technologies: ['Laravel', 'PHP', 'MVC', 'Git', 'Trello'],
    image: '/projects/adolices.png',
    color: '#55d6be',

  },
  {
    number: '03',
    title: 'BioPoint',
    category: 'Data · Recherche',
    description:
      "Développement d'une chaîne d'acquisition et d'analyse de données physiologiques permettant d'étudier la réponse de l'organisme après exposition à différentes types de pollution sonore.",
    technologies: ['Python', 'ECG', 'EDA', 'EMG', 'Signal Processing'],
    image: '/projects/biopoints.jpg',
    color: '#f5b942',

  }
]
</script>


<template>

  <section id="projects" class="projects">

    <div class="projects-stars">
      <span
        v-for="star in stars"
        :key="star.id"
        class="projects-star"
        :style="{
          left: `${star.x}%`,
          top: `${star.y}%`,
          width: `${star.size}px`,
          height: `${star.size}px`,
          animationDelay: `${star.delay}s`
        }"
      ></span>
</div>

    <div class="projects-content">

      <div class="projects-title">
        <span>03</span>
        <h2>Projets</h2>
      </div>

      <div class="projects-list">

        <article
          v-for="(project, index) in projects"
          :key="project.title"
          class="project"
          :class="{ reverse: index % 2 === 1 }"
          :style="{ '--project-color': project.color }"
        >

          <div class="project-image">

            <img
              :src="project.image"
              :alt="project.title"
            />

          </div>

          <div class="project-info">

            <span class="project-number">
              {{ project.number }}
            </span>

            <span class="project-category">
              {{ project.category }}
            </span>

            <h3>
              {{ project.title }}
            </h3>

            <p>
              {{ project.description }}
            </p>

            <div class="project-technologies">

              <span
                v-for="technology in project.technologies"
                :key="technology"
              >
                {{ technology }}
              </span>

            </div>

          </div>

        </article>

      </div>

    </div>

  </section>

</template>