<script setup lang="ts">
import { ref, onMounted} from 'vue'

const currentExperience = ref(0)
const direction = ref<'next' | 'prev'>('next')

const stars = ref<
  { id: number; x: number; y: number; size: number; delay: number }[]
>([])

const experiences = [
  {
    year: 'Septembre 2025 - Mars 2026',
    company: 'Amaris Mantu',
    role: 'Stagiaire Développeur Front-End',
    color: '#800080',
    location: 'Strasbourg, France',
    description:
      "Développement Front-End d'une application web dynamique en Angular. \nConception et adaptation de maquettes en interfaces fonctionnelles et travail en collaboration avec une équipe de développeurs Front-End, Back-End et Full-Stack.",
    technologies: ['Angular', 'TypeScript', 'HTML / SCSS', 'Git']
  },
  {
    year: 'Mars – Juillet 2026',
    company: 'Université de Sherbrooke',
    role: 'Stagiaire de recherche',
    location: 'Québec, Canada',
    color: '#90EE90',
    description:
      "Conception et mise en œuvre de protocoles expérimentaux. Collecte et traitement de données physiologiques et environnementales, analyse des données et automatisation des traitements. Travail en collaboration avec des chercheurs et doctorants.",
    technologies: ['Python', 'Analyse de données', 'Expérimentation', 'Automatisation']
  },
    {
    year: 'Avril – Août 2025',
    company: 'Hypno VR',
    role: 'Stagiaire Data Analyst',
    location: 'Strasbourg, France',
    color: '#ADD8E6',
    description:
      "Exploration et compréhension de données issues du secteur de la santé. Nettoyage et harmonisation de la base de données avec Power Query et SQL, puis création de tableaux de bord dynamiques dans Power BI. Collaboration avec les équipes métiers pour identifier et répondre à leurs besoins.",
    technologies: ['Power BI','DAX', 'Power Query', 'SQL', 'Data Analysis']
  },
    {
    year: 'Mai – Août 2024',
    company: 'ARTE',
    role: 'Stagiaire Data Analyst / Data Engineer',
    location: 'Strasbourg, France',
    color: '#FFA500',
    description:
      "Récolte et gestion de données avec Databricks SQL. Développement et automatisation de rapports BI avec Power BI. Travail en environnement Agile et participation à l'organisation des équipes.",
    technologies: ['Python','Databricks SQL', 'Power BI', 'JIRA', 'Agile / Scrum']
  },

]

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

function nextExperience() {
  direction.value = 'next'

  currentExperience.value =
    (currentExperience.value + 1) % experiences.length
}

function previousExperience() {
  direction.value = 'prev'

  currentExperience.value =
    (currentExperience.value - 1 + experiences.length) %
    experiences.length
}
</script>

<template>
  <section id="experience" class="experience">

          <!-- Ciel étoilé -->
    <div class="experience-stars">
      <span
        v-for="star in stars"
        :key="star.id"
        class="experience-star"
        :style="{
          left: `${star.x}%`,
          top: `${star.y}%`,
          width: `${star.size}px`,
          height: `${star.size}px`,
          animationDelay: `${star.delay}s`
        }"
      ></span>
    </div>

    <div class="experience-content">

      <!-- Titre -->
      <div class="experience-title">
        <span>02</span>
        <h2>Expériences</h2>
      </div>

      <!-- Carousel -->
      <div class="experience-carousel">

        <!-- Flèche gauche -->
        <button
          class="carousel-arrow carousel-arrow-left"
          @click="previousExperience"
          aria-label="Expérience précédente"
        >
          ←
        </button>

        <!-- Carte -->
        <Transition :name="direction" mode="out-in">
          <article
               :key="currentExperience"
                class="experience-card"
                :style="{
                 '--experience-color': experiences[currentExperience].color
                }"
            >

            <div class="experience-card-header">
              <span class="experience-year">
                {{ experiences[currentExperience].year }}
              </span>

              <span class="experience-location">
                {{ experiences[currentExperience].location }}
              </span>
            </div>

            <div class="experience-card-content">

              <p class="experience-company">
                {{ experiences[currentExperience].company }}
              </p>

              <h3>
                {{ experiences[currentExperience].role }}
              </h3>

              <p class="experience-description">
                {{ experiences[currentExperience].description }}
              </p>

              <div class="experience-tags">
                <span
                  v-for="technology in experiences[currentExperience].technologies"
                  :key="technology"
                >
                  {{ technology }}
                </span>
              </div>

            </div>

          </article>
        </Transition>

        <!-- Flèche droite -->
        <button
          class="carousel-arrow carousel-arrow-right"
          @click="nextExperience"
          aria-label="Expérience suivante"
        >
          →
        </button>

      </div>

      <!-- Indicateurs -->
      <div class="carousel-indicators">

        <button
          v-for="(_, index) in experiences"
          :key="index"
          :class="{ active: currentExperience === index }"
          @click="currentExperience = index"
          :aria-label="`Afficher l'expérience ${index + 1}`"
        ></button>

      </div>

    </div>

  </section>
</template>