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
</script>


<template>
  <section id="contact" class="contact">
    <div class="contact-content">

        <span
        v-for="star in stars"
        :key="star.id"
        class="contact-star"
        :style="{
          left: `${star.x}%`,
          top: `${star.y}%`,
          width: `${star.size}px`,
          height: `${star.size}px`,
          animationDelay: `${star.delay}s`
        }"
      ></span>

      <div class="contact-title">
        <span>05</span>
        <h2>Contact</h2>
      </div>

      <div class="contact-main">
        <div class="contact-intro">
          <p class="contact-status">
            DISPONIBLE À PARTIR DE MARS 2027
          </p>

          <h3>Un projet ou une opportunité ?</h3>

          <p>
            Je recherche actuellement un stage de fin d'études de 6 mois
            dans le domaine du développement informatique, de l'algorithmique
            et de la data.
          </p>

          <p class="contact-location">
            Je suis actuellement au Mexique dans le cadre de mon semestre
            académique. Pour me contacter, je privilégie donc les échanges
            par <strong>mail ou WhatsApp</strong>.
          </p>
        </div>

        <div class="contact-links">

          <a
            href="mailto:samy.isik.67@gmail.com"
            class="contact-link"
          >
            <span class="contact-label">MAIL</span>
            <span class="contact-value">
              samy.isik.67@gmail.com
            </span>
          </a>

          <a
            href="https://wa.me/33762078543"
            target="_blank"
            rel="noopener noreferrer"
            class="contact-link"
          >
            <span class="contact-label">WHATSAPP</span>
            <span class="contact-value">
              +33 7 62 07 85 43
            </span>
          </a>

          <a
            href="https://www.linkedin.com/in/samy-isik-72940b323/"
            target="_blank"
            rel="noopener noreferrer"
            class="contact-link"
          >
            <span class="contact-label">LINKEDIN</span>
            <span class="contact-value">
              Mon profil LinkedIn ↗
            </span>
          </a>

        </div>
      </div>

    </div>
  </section>
</template>