<script setup lang="ts">
import { ref } from 'vue'

const modules = import.meta.glob('../pages/**/*.vue')

const routes = Object.keys(modules)
  .map(p =>
    p
      .replace(/^\.{1,2}\//, '')   // enlève "./" ou "../"
      .replace(/^pages\//, '')     // enlève "pages/"
      .replace(/\.vue$/, '')       // enlève l'extension
      .replace(/\/?index$/, '')    // enlève "index" (avec ou sans / avant)
  )
  .map(slug => '/' + slug)    

const links = routes.map(route => ({
  route,
  label:
    route === '/'
      ? 'Accueil'
      : route
          .split('/').pop()!          
          .replace(/[-_]/g, ' ')     
          .replace(/^./, c => c.toUpperCase()) 
}))

const hoveredLink = ref('')

const reqUrl = useRequestURL();

useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "WebPage",
  name: "Derniers projets de création de sites Web à Chambéry",
  description:
    "Nos tous derniers projets de création de sites Internet à Chambéry.",
  url: reqUrl.href,
}));

useHead(() => ({
  title: "Plan du site | Tekila Web Factory",
  meta: [
    {
      name: "description",
      content:
        "Plan du site | Création de sites Internet à Chambéry, en Savoie.",
    },
    {
      property: "og:title",
      content: "Plan du site | Tekila Web Factory",
    },
    {
      property: "og:description",
      content:
        "Plan du site | Création de sites Internet à Chambéry, en Savoie.",
    },
  ],
}));
</script>
<template>
  <section class="plan">
    <div class="plan__headlines">
      
      <h1 class="plan__headlines__small">
        Tous les liens vers les pages de notre site Web
      </h1>
      <span class="plan__headlines__title">Plan du site</span>
    </div>

    <ul class="plan__links">
      <li class="plan__links__link" v-for="link in links" :key="link.label" @mouseenter="hoveredLink = link.label" @mouseleave="hoveredLink = ''">
        <NuxtLink :to="link.route"
          >{{ link.label
          }}<IconComponent icon="arrow-up-right-bold" size="1.375rem" :color="hoveredLink === link.label ? colors['accent-color'] : colors['text-color']" />
          </NuxtLink
        />
  
      </li>
    </ul>
  </section>
    <InfoBanner />
</template>
<style lang="scss" scoped>
.plan {
  display: flex;
  flex-direction: column;
  padding: 4rem 2rem;
  gap: 1rem;
  background-color: $base-color;

  @media (min-width: $big-tablet-screen) {
    padding: 8rem 4rem;
    gap: 2rem;
  }

  &__headlines {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    color: $text-color;
    color: $text-color;
    height: fit-content;

    &__small {
      font-size: $subtitles-size-1;
      font-weight: $regular;
    }

    &__title {
      font-size: $titles-size-1;
      font-weight: $bold;
      text-wrap: balance;

      @media (min-width: $big-tablet-screen) {
        font-size: $titles-size-3;
      }
    }
  }

  &__links {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    list-style: none;
    color: $text-color;

    &__link {
      & a {
        display: flex;
        gap: 0.25rem;
        color: $text-color;
        font-size: $text-size-3;
        font-weight: $regular;
        align-items: end;
        
      }
    }
  }
}
</style>
