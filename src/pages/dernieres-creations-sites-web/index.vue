<script lang="ts">
import InfoBanner from "~/components/InfoBanner.vue";
import PrimaryButton from "~/components/PrimaryButton.vue";

useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "WebPage",
  name: "Derniers projets de création de sites Web à Chambéry",
  description:
    "Nos tous derniers projets de création de sites Internet à Chambéry.",
  url: window.location.href,
}));

useHead(() => ({
  title: "Derniers projets de création de sites Web à Chambéry",
  meta: [
    {
      name: "description",
      content:
        "Nos tous derniers projets de création de sites Internet à Chambéry.",
    },
    {
      property: "og:title",
      content: "Derniers projets de création de sites Web à Chambéry",
    },
    {
      property: "og:description",
      content:
        "Nos tous derniers projets de création de sites Internet à Chambéry.",
    },
  ],
}));
</script>
<template>
  <section class="split-banner">
    <picture class="split-banner__image">
      <source
        srcset="@/assets/images/sofar-banner.webp"
        media="(min-width: 1100px)"
      />
      <source
        media="(min-width: 600px)"
        srcset="@/assets/images/sofar-banner-tablet.webp"
      />
      <img
        src="@/assets/images/sofar-banner-mobile.webp"
        alt="création sites internet"
      />
      <div class="split-banner__image__headlines">
        <img
          class="split-banner__image__headlines__logo"
          src="@/assets/images/logo-sofar.svg"
          alt="logo sofar private jet"
        />
        <h2 class="split-banner__image__headlines__tag">Site Web vitrine</h2>
        <p class="split-banner__image__headlines__description">
          Refonte d'un site Internet Wix pour Sofar, une entreprise de fret de
          jet privés basée aux États-Unis.
        </p>
        <NuxtLink to="https://flysofar.com" target="_blank" dofollow>
          <PrimaryButton variant="secondary-color" icon="arrow-right-bold">
            Voir le site Web
          </PrimaryButton></NuxtLink
        >
      </div>
    </picture>

    <picture class="split-banner__image">
      <source
        srcset="@/assets/images/jp-banner.webp"
        media="(min-width: 1100px)"
      />
      <source
        media="(min-width: 600px)"
        srcset="@/assets/images/jp-banner-tablet.webp"
      />
      <img
        src="@/assets/images/jp-banner-mobile.webp"
        alt="création sites internet"
      />
      <div class="split-banner__image__headlines">
        <img
          class="split-banner__image__headlines__logo"
          src="@/assets/images/logo-jp.svg"
          alt="logo jp ebenisterie"
        />

        <h2 class="split-banner__image__headlines__tag">Site Web vitrine</h2>
        <p class="split-banner__image__headlines__description">
          Création d'un site Internet pour JP Ébénisterie, l'entreprise d'un
          artisan ébéniste basé à Chambéry.
        </p>
        <NuxtLink to="https://jpebenisterie73.fr" target="_blank" dofollow>
          <PrimaryButton variant="secondary-color" icon="arrow-right-bold">
            Voir le site Web
          </PrimaryButton></NuxtLink
        >
      </div>
    </picture>
  </section>
  <InfoBanner />
</template>
<style lang="scss" scoped>
.split-banner {
  display: flex;
  flex-direction: column;

  @media (min-width: $laptop-screen) {
    flex-direction: row;
  }

  &__image {
    width: 100%;
    height: 100vh;
    transition: width 0.2s linear;
    position: relative;

    &::after {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba($text-color, 0.4);
      z-index: 0;
    }

    @media (min-width: $laptop-screen) {
      width: 50%;

      &:hover {
        cursor: pointer;
      }
    }

    &__headlines {
      display: flex;
      z-index: 1;
      position: absolute;
      flex-direction: column;
      gap: 1rem;
      left: 0;
      bottom: 0;
      height: fit-content;
      width: 100%;
      margin: auto;
      justify-content: center;
      padding: 1rem;

      @media (min-width: $laptop-screen) {
        gap: 2rem;
        padding: 4rem;
      }

      &__tag {
        display: flex;
        background-color: $text-color;
        color: $text-color-alt;
        font-size: $text-size-2;
        font-weight: $regular;
        padding: 1rem 2rem;
        white-space: nowrap;
        justify-content: flex-end;
        width: fit-content;
        position: relative;
        max-height: 54px;
        min-height: 54px;
      }

      &__logo {
        width: 180px;
        max-width: 180px;
        height: 140px;
        max-height: 140px;
        object-fit: cover;
        object-position: center;
        margin: auto;
        margin-bottom: 1rem;

        @media (min-width: $laptop-screen) {
          margin-bottom: 2rem;
        }
      }

      &__description {
        display: flex;
        color: $text-color-alt;
        font-size: $subtitles-size-2;
        font-weight: $bold;
        border-radius: 0.4rem;
        text-wrap: balance;

        @media (min-width: $big-tablet-screen) {
          font-size: $titles-size-1;
        }

        @media (min-width: $laptop-screen) {
          font-size: $subtitles-size-2;
        }

        @media (min-width: $desktop-screen) {
          font-size: $titles-size-1;
        }
      }
    }

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    source {
      display: none;
    }
  }
}
</style>
