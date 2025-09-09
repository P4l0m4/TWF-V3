<script setup lang="ts">
const reqUrl = useRequestURL();

useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "WebPage",
  name: "Questions courantes sur la création de sites Web",
  description:
    "Questions courantes sur la création de sites Web à Chambéry, en Savoie.",
  url: reqUrl.href,
}));

useHead(() => ({
  title: "Questions courantes sur la création de sites Web",
  meta: [
    {
      name: "description",
      content:
        "Création de sites Internet à Chambéry, en Savoie. Pas d'abonnement, pas de frais cachés.",
    },
    {
      property: "og:title",
      content: "Questions courantes sur la création de sites Web",
    },
    {
      property: "og:description",
      content:
        "Questions courantes sur la création de sites Web à Chambéry, en Savoie.",
    },
  ],
}));
</script>
<template>
  <FAQ />
  <InfoBanner />
</template>
