<script setup>
import { colors } from "@/utils/colors.ts";
import bang from "@/assets/images/bang.webp";
import art from "@/assets/images/art.webp";
import run from "@/assets/images/run.webp";
import look from "@/assets/images/look.webp";

useJsonld(() => ({
  "@context": "https://schema.org/",
  "@type": "Product",
  name: "Site vitrine",
  image: "",
  description:
    "Création d'un site web basique. Pages essentielles, design sur mesure, hébergement performant et outils indispensables.",
  brand: {
    "@type": "Brand",
    name: "Tekila Web Factory",
  },
  aggregateRating: {
    "@type": "AggregateRating",
    ratingValue: "5",
    bestRating: "5",
    worstRating: "5",
    ratingCount: "10",
  },
}));

const features = [
  {
    title: "Pages essentielles",
    details:
      "Accueil | Qui sommes nous | Que faisons nous | Contact. Ou d'autres, c'est vous qui décidez qu'elles pages vous voulez sur votre site Web.",
    image: bang,
  },
  {
    title: "Design sur mesure",
    details:
      "On réalise des maquettes sur mesure pour votre site Internet, spécialement pensées pour correspondre à votre projet. Pas de design copier-coller.",
    image: art,
  },
  {
    title: "Hébergement performant",
    details:
      "Vous n'aurez jamais à payer l'Hébergement de votre site Web, et ça, on vous le garanti.",
    image: run,
  },
  {
    title: "Outils indispensables",
    details:
      "On connecte votre site Internet aux outils d'analyse essentiels pour que vous puissiez mesurer votre succès en ligne.",
    image: look,
  },
];
</script>

<template>
  <section id="tarifs" class="pricing">
    <div class="pricing__headlines">
      <h2 class="pricing__headlines__title">
        Un site Web basique, c'est combien ?
      </h2>
      <div class="pricing__price">
        Chez nous, c'est
        <span class="pricing__price__number">1800 €</span>
        et pas un centime de plus.
      </div>
    </div>
    <div class="pricing__cards">
      <div class="pricing__cards__card">
        <ul class="pricing__cards__card__features">
          <li
            class="pricing__cards__card__features__feature"
            v-for="feature in features"
            :key="feature.title"
          >
            <img
              class="pricing__cards__card__features__feature__image"
              :src="feature.image"
              alt="tarifs site internet"
            />
            <span class="pricing__cards__card__features__feature__title">{{
              feature.title
            }}</span>
            <span class="pricing__cards__card__features__feature__details">{{
              feature.details
            }}</span>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.pricing {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 2rem 1rem;

  @media (min-width: $big-tablet-screen) {
    gap: 4rem;
    padding: 4rem;
  }

  &__headlines {
    display: flex;
    flex-direction: column;
    gap: 2rem;

    &__title {
      font-size: $subtitles-size-1;
      font-weight: $regular;

      @media (min-width: $big-tablet-screen) {
        font-size: $subtitles-size-2;
      }
    }
  }

  &__cards {
    display: flex;
    gap: 1rem;
    width: 100%;

    @media (min-width: $big-tablet-screen) {
      gap: 2rem;
    }

    &__card {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      width: 100%;

      @media (min-width: $big-tablet-screen) {
        gap: 2rem;
        flex-direction: row;
      }

      &__features {
        list-style: none;
        display: grid;
        gap: 2rem;
        width: 100%;
        grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));

        @media (min-width: $big-tablet-screen) {
          gap: 4rem;
          grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
        }

        &__feature {
          display: flex;
          flex-direction: column;
          gap: 1rem;
          width: fit-content;

          @media (min-width: $big-tablet-screen) {
            gap: 2rem;
          }

          &__image {
            width: 100%;
            height: 300px;
            object-position: center;
            object-fit: cover;
            border-radius: 30% 0;

            @media (min-width: $big-tablet-screen) {
              width: 100%;
              height: 350px;
            }
          }

          &__title {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-weight: $bold;
            font-size: $titles-size-1;
            color: $text-color;
            text-wrap: balance;
          }

          &__details {
            font-weight: $regular;
            font-size: $text-size-1;
          }
        }
      }

      &__button {
        background-color: $secondary-color;
        color: $primary-color;
        box-shadow: $shadow;

        &:nth-of-type(3) {
          background-color: $primary-color;
          color: $primary-color;
        }
      }
      &__link {
        margin-top: -0.5rem;
        text-align: center;

        @media (min-width: $big-tablet-screen) {
          margin-top: -1rem;
        }
      }
    }
  }

  &__price {
    font-size: $titles-size-1;
    font-weight: $regular;

    &__number {
      position: relative;

      &::before {
        content: "";
        display: block;
        background-color: $accent-color;
        opacity: 0.25;
        width: 80%;
        height: 2rem;
        z-index: -1;
        position: absolute;
        transform: rotate(-3deg);
        inset: 0;
        top: 0.5rem;
      }

      &::after {
        content: "TTC";
        margin-left: 0.5rem;
        font-size: $text-size-1;
        font-weight: $regular;
      }
    }
  }
}
</style>
