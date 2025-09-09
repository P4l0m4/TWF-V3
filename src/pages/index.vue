<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from "vue";
import { isDesktop } from "~/utils/functions";

const desktopScreen = ref(false);

onMounted(() => {
  desktopScreen.value = isDesktop();

  window.addEventListener("resize", () => {
    desktopScreen.value = isDesktop();
  });
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", () => {
    desktopScreen.value = isDesktop();
  });
});

const argumentsList = [
  {
    title: "Service client réactif 7j/7",
    description:
      "Nous voulons que nos clients continuent à nous recommander, donc nous ne les laissons jamais tomber; même le week-end et les jours fériés. ",
  },
  {
    title: "Pas de (mauvaises) surprises",
    description:
      "Pas d'abonnements ni de frais cachés. Votre nom de domaine sera la seule chose que vous devrez renouveler.",
  },
  {
    title: "Design optimisé pour convaincre",
    description:
      "Le design de nos sites Internet est réalisé sur mesure et pensé spécialement pour convertir vos visiteurs en clients.",
  },
  {
    title: "Équipe expérimentée",
    description:
      "De la création de site Internet et de boutiques en ligne au développement d'outils scientifiques, nous maîtrisons notre sujet et comprenons vos problématiques.",
  },
  {
    title: "Suivi et statistiques",
    description:
      "Nous connectons votre site Web à des outils de reccueil et d'analyse pour vous aider à mesurer votre succès sur Internet.",
  },
  {
    title: "Confort et accessibilité",
    description:
      "Nous créons des sites Web fluides et agréables à utiliser. Pas de bugs, d'animations qui sautent partout, ni de pop-ups intrusives.",
  },
  {
    title: "Visibilité garantie 24/7",
    description:
      "Votre site Web est accessible en continu, et s'affiche parfaitement sur tous les écrans de PC, tablettes et mobiles.",
  },
];

const dataList = [
  {
    title: "4 Mois",
    subtitle: "Temps moyen pour rentabiliser votre site Web ",
  },
  {
    title: "100%",
    subtitle: "Taux de satisfaction de nos clients, en France et à l'étranger",
  },
  {
    title: "14,1%",
    subtitle: "CTR Moyen (taux de clic après apparition sur la SERP)",
  },
  {
    title: "5",
    subtitle:
      "Position moyenne sur la SERP (page de résultats de recherche Google)",
  },
];

const reqUrl = useRequestURL();

useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "WebPage",
  name: "Création de sites Web à Chambéry, en Savoie",
  description:
    "Création de sites Internet à Chambéry, en Savoie. Pas d'abonnement, pas de frais cachés.",
  url: reqUrl.href,
}));

useHead(() => ({
  title: "Création de sites Web à Chambéry, en Savoie",
  meta: [
    {
      name: "description",
      content:
        "Création de sites Internet à Chambéry, en Savoie. Pas d'abonnement, pas de frais cachés.",
    },
    {
      property: "og:title",
      content: "Création de sites Web à Chambéry, en Savoie",
    },
    {
      property: "og:description",
      content:
        "Création de sites Internet à Chambéry, en Savoie. Pas d'abonnement, pas de frais cachés.",
    },
  ],
}));
</script>
<template>
  <picture class="banner">
    <source media="(min-width: 1100px)" srcset="@/assets/images/banner.webp" />
    <source
      media="(min-width: 600px)"
      srcset="@/assets/images/banner-tablet.webp" />
    <div class="headlines">
      <span class="headlines__small">Des sites simples, pro, efficaces</span>
      <h1 class="headlines__title">
        Création de sites Web à Chambéry, en Savoie
      </h1>
      <NuxtLink
        to="https://calendar.app.google/q4vewDNVHKHNjyDG6"
        target="_blank"
        v-if="!desktopScreen"
        style="margin-top: 1rem"
        ><PrimaryButton variant="secondary-color" icon="chat-circle-bold"
          >Prendre rendez-vous
        </PrimaryButton>
      </NuxtLink>
    </div>
    <img
      class="index__banner__img"
      src="@/assets/images/banner-mobile.webp"
      alt="banner image"
  /></picture>
  <section id="why-choose-us" class="why-choose-us">
    <h2 class="why-choose-us__title">Pourquoi nous confier votre site Web ?</h2>
    <div class="why-choose-us__grid">
      <div
        class="why-choose-us__grid__argument"
        v-for="argument in argumentsList"
        :key="argument.title"
      >
        <h3 class="why-choose-us__grid__argument__title">
          {{ argument.title }}
        </h3>
        <p class="why-choose-us__grid__argument__description">
          {{ argument.description }}
        </p>
      </div>
    </div>
  </section>
  <section class="data">
    <div class="data__item" v-for="data in dataList" :key="data.title">
      <span class="data__item__title">{{ data.title }}</span>
      <span class="data__item__subtitle">{{ data.subtitle }}</span>
    </div>
  </section>
  <PricingComponent />
  <InfoBanner />
  <QuiSommesNous />
  <QuestionComponent />
</template>
<style lang="scss">
.why-choose-us {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 2rem 1rem;

  @media (min-width: $big-tablet-screen) {
    padding: 4rem;
    gap: 2rem;
  }

  &__title {
    font-weight: $regular;
    font-size: $text-size-2;

    @media (min-width: $big-tablet-screen) {
      font-size: $text-size-3;
    }
  }

  &__grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1rem;

    @media (min-width: $big-tablet-screen) {
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 2rem;
    }

    &__argument {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      background-color: $primary-color;
      border-radius: $radius;
      padding: 1rem;
      @media (min-width: $big-tablet-screen) {
        padding: 2rem;
        gap: 2rem;
      }

      &__title {
        font-size: $subtitles-size-2;
        font-weight: $bold;
        @media (min-width: $big-tablet-screen) {
          font-size: $titles-size-1;
        }
      }

      &__description {
        font-size: $text-size-2;
        font-weight: $regular;
      }
    }
  }
}

.data {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 4rem;
  background-color: $accent-color;
  padding: 2rem 1rem;

  @media (min-width: $big-tablet-screen) {
    padding: 2rem 4rem;
  }

  &__item {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    color: $primary-color;
    justify-content: center;

    &__title {
      font-size: $titles-size-2;
      font-weight: $bold;
    }

    &__subtitle {
      font-size: $text-size-2;
      font-weight: $regular;
    }
  }
}
</style>
