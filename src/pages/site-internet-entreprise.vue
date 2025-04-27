<script setup lang="ts">
useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "WebPage",
  name: "Création de site internet entreprise",
  description:
    "Création de site internet pour les entreprises à Chambéry, en Savoie. Pas d'abonnement, pas de frais cachés.",
  url: window.location.href,
}));

useHead(() => ({
  title: "Création de site internet entreprise",
  meta: [
    {
      name: "description",
      content: "",
    },
    {
      property: "og:title",
      content:
        "Création de sites internet pour les entreprises à Chambéry, en Savoie",
    },
    {
      property: "og:description",
      content:
        "Création de sites internet pour les entreprises à Chambéry, en Savoie. Pas d'abonnement, pas de frais cachés.",
    },
  ],
}));
</script>
<template>
  <picture class="banner">
    <source
      media="(min-width: 1100px)"
      srcset="@/assets/images/company-banner.webp" />
    <div class="headlines">
      <span class="headlines__small">Des sites simples, pro, efficaces</span>
      <h1 class="headlines__title">Site internet entreprise</h1>
    </div>
    <img
      class="index__banner__img"
      src="@/assets/images/company-banner-mobile.webp"
      alt="banner image"
  /></picture>
  <InfoBanner />
</template>
<style lang="scss" scoped>
.banner {
  &::after {
    content: "";
    display: block;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 0;
    background-image: linear-gradient(
      -45deg,
      rgba($secondary-color, 0.6),
      transparent 80%
    );
  }
}
</style>
