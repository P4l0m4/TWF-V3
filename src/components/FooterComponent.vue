<script setup lang="ts"></script>
<template>
  <footer class="footer">
    <div class="footer__text">
      <div class="footer__text__column">
        <NuxtLink to="/" class="logo noselect"
          ><img
            src="@/assets/images/logotwf-small-light.svg"
            alt="logo tekila web factory"
        /></NuxtLink>
        <p>
          Creation de sites Web à Chambéry, en Savoie. Nous créon tous types de
          sites Web sur mesure, boutiques en ligne et outils personnalisés.
        </p>
        <div class="footer__text__column__row-links">
          <NuxtLink
            to="https://calendar.app.google/q4vewDNVHKHNjyDG6"
            target="_blank"
            style="text-decoration: underline"
            >Prendre rendez-vous</NuxtLink
          >
        </div>
        <!-- <div class="footer__text__column__row-links">
          <NuxtLink to="/ameublement-professionnel-savoie"
            >Ameublement professionnel</NuxtLink
          ><NuxtLink to="/ameublement-particuliers-savoie"
            >Ameublement pour particuliers</NuxtLink
          >
        </div> -->
        <!-- <div class="footer__text__column__row-links">
          <NuxtLink
            to="/outil-materiaux-meubles-sur-mesure"
            style="text-decoration: underline"
            >Matériaux à partir d'une image</NuxtLink
          >

          <NuxtLink to="/autres-meubles-sur-mesure"
            >Autres meubles sur mesure</NuxtLink
          >
        </div> -->
      </div>
      <!-- <ul class="footer__text__column">
        <li class="footer__text__column__link">
          <NuxtLink to="/cuisine-sur-mesure-savoie" class="nuxt-link"
            >Cuisine sur mesure</NuxtLink
          >
        </li>
      </ul> -->
      <ul class="footer__text__column">
        <!-- <li class="footer__text__column__link">
          <NuxtLink to="/contact-ebeniste-savoie#faq" class="nuxt-link"
            >F.A.Q.</NuxtLink
          >
        </li> -->

        <!-- <li class="footer__text__column__link">
          <NuxtLink
            to="/prestations-ebenisterie-savoie"
            class="nuxt-link"
            style="opacity: 0.6; pointer-events: none"
            >Prestations</NuxtLink
          >
        </li> -->
      </ul>
    </div>
    <div class="footer__bottom">
      <span>©Tekila Web Factory 2025</span>
      <!-- <div class="icons">
        <a href="facebook.com" aria-label="Facebook" target="_blank">
          <IconComponent
            icon="facebook-logo-fill"
            :color="colors['textColor']"
            size="20px"
          />
        </a>
        <a
          href="https://www.instagram.com/jp.ebenisterie73?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw=="
          aria-label="Instagram"
          target="_blank"
        >
          <IconComponent
            icon="instagram-logo-fill"
            :color="colors['chocolate-martini']"
            size="20px"
        /></a>
      </div> -->
      <span style="margin-left: auto">Mentions légales</span>
    </div>
  </footer>
</template>
<style lang="scss" scoped>
.footer {
  background-color: $text-color;
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
    color: $secondary-color;
    flex-wrap: wrap;

    a {
      color: $secondary-color;
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

.icons {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}
</style>
