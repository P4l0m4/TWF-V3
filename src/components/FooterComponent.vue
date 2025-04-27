<script setup lang="ts"></script>
<template>
  <footer class="footer">
    <div class="footer__text">
      <div class="footer__text__column">
        <NuxtLink to="/" class="logo noselect"
          ><img
            src="@/assets/images/logotwf-light.svg"
            alt="logo tekila web factory"
        /></NuxtLink>
        <p>
          Creation de sites Web à Chambéry, en Savoie. Nous créons tous types de
          sites Web sur mesure, boutiques en ligne et outils personnalisés.
        </p>
        <div class="footer__text__column__row-links">
          <NuxtLink
            to="https://calendar.app.google/q4vewDNVHKHNjyDG6"
            target="_blank"
            style="text-decoration: underline"
            >Prendre rendez-vous avec nous</NuxtLink
          >
        </div>
      </div>
      <div class="footer__text__column">
        <NuxtLink to="#tarifs" class="footer__text__column__link"
          >Tarifs</NuxtLink
        ><NuxtLink
          to="#process"
          class="footer__text__column__link"
          style="opacity: 0.5; pointer-events: none"
          >Process</NuxtLink
        >
        <NuxtLink to="#who-we-are" class="footer__text__column__link"
          >Qui sommes nous ?</NuxtLink
        >
        <NuxtLink
          to="/questions-courantes-sur-la-creation-de-sites-web"
          class="footer__text__column__link"
          >Questions courantes</NuxtLink
        >
        <NuxtLink to="#why-choose-us" class="footer__text__column__link"
          >Pourquoi nous choisir ?</NuxtLink
        >
      </div>
      <div class="footer__text__column">
        <NuxtLink
          to="/site-internet-entreprise"
          class="footer__text__column__link"
          style="opacity: 0.5; pointer-events: none"
          >Sites internet d'entreprise</NuxtLink
        >
        <NuxtLink
          to="/site-internet-sans-abonnement"
          class="footer__text__column__link"
          style="opacity: 0.5; pointer-events: none"
          >Sites internet sans abonnement</NuxtLink
        >
      </div>
    </div>
    <div class="footer__bottom">
      <span>©Tekila Web Factory 2025</span>

      <NuxtLink to="documents/mentions-legales.pdf" target="_blank"
        >Mentions légales</NuxtLink
      >
      <NuxtLink to="/plan-du-site">Plan du site</NuxtLink>
    </div>
  </footer>
</template>
<style lang="scss" scoped>
.footer {
  background-color: $secondary-color;
  display: flex;
  padding: 2rem;
  flex-direction: column;
  gap: 4rem;

  @media (min-width: $big-tablet-screen) {
    padding: 4rem;
  }

  &__text {
    display: flex;
    gap: 4rem;
    width: 100%;
    justify-content: space-between;
    flex-wrap: wrap;
    align-items: end;

    &__column {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      max-width: 496px;
      list-style: none;
      color: $base-color;

      &__row-links {
        display: flex;
        justify-content: space-between;
        gap: 1rem;
        align-items: center;
        flex-wrap: wrap;

        a {
          color: $base-color;
          white-space: nowrap;
        }
      }

      &__link {
        color: $base-color;

        .nuxt-link {
          color: $base-color;
        }
      }
    }
  }

  &__bottom {
    display: flex;
    gap: 1rem;
    color: $accent-color;
    flex-wrap: wrap;
    border-top: 1px solid $accent-color;
    padding-top: 2rem;

    a {
      color: $accent-color;
      white-space: nowrap;
      @media (min-width: $big-tablet-screen) {
        margin-left: auto;
      }
    }
  }
}

.logo {
  margin-bottom: 1rem;

  & img {
    height: 50px;
  }
}
</style>
