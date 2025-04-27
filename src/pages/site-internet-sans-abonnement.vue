<script setup lang="ts">
useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "WebPage",
  name: "Site internet sans abonnement",
  description: "Site internet sans abonnement à Chambéry, en Savoie.",
  url: window.location.href,
}));

useHead(() => ({
  title: "Site internet sans abonnement",
  meta: [
    {
      name: "description",
      content: "Site internet sans abonnement à Chambéry, en Savoie.",
    },
    {
      property: "og:title",
      content: "Site internet sans abonnement",
    },
    {
      property: "og:description",
      content: "Site internet sans abonnement à Chambéry, en Savoie.",
    },
  ],
}));
</script>
<template>
  <picture class="banner">
    <source media="(min-width: 1100px)" srcset="@/assets/images/banner.webp" />
    <div class="headlines">
      <span class="headlines__small">Des sites simples, pro, efficaces</span>
      <h1 class="headlines__title">Site internet sans abonnement</h1>
    </div>
    <img
      class="index__banner__img"
      src="@/assets/images/banner-mobile.webp"
      alt="banner image"
  /></picture>
  <InfoBanner />
</template>
