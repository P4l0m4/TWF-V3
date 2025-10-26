<script setup lang="ts">
import { colors } from "@/utils/colors";

const faq = [
  {
    title: "Combien de temps faut-il pour créer un site web ?",
    answer:
      "En moyenne, il faut entre 4 semaines et 3 mois pour créer un site web. Cela dépend de la complexité du projet et de la disponibilité des informations.",
  },
  {
    title: "Comment savoir si ça vaut le coup de créer un site Internet ?",
    answer:
      "Créer un site web est particulièrement utile si votre activité a besoin de visibilité, de crédibilité ou d’automatisation.",
  },
  {
    title: "J'ai déjà un site Internet, mais je veux le changer. Que faire ?",
    answer:
      "Pas de souci ! Nous pouvons vous aider à migrer votre site Internet vers une nouvelle plateforme ou à le refondre complètement. Passez nous un petit coup de fil et nous vous aiderons à trouver la meilleure solution.",
  },
  {
    title: "Faites-vous des sites Internet en plusieurs langues ?",
    answer: "Oui, nous pouvons créer des sites Internet multilingues.",
  },
  {
    title: "Est-ce que je peux gérer mon site Internet moi-même ?",
    answer:
      "Oui, nous vous formons à l'utilisation de votre site Internet afin que vous puissiez le gérer vous-même. Nous restons également disponibles pour vous aider si besoin.",
  },
  {
    title: "Est-ce que je peux changer d'hébergeur ?",
    answer:
      "Oui, vous pouvez changer d'hébergeur à tout moment. Nous travaillons avec Netlify et Vercel, mais nous pouvons également vous aider à migrer vers d'autres hébergeurs.",
  },
  {
    title: "Est-ce que je peux changer de nom de domaine ?",
    answer:
      "Vous pouvez changer de nom de domaine à tout moment. Nous vous aiderons à migrer votre site vers le nouveau nom de domaine.",
  },
  {
    title: "Est-ce que je peux changer de prestataire ?",
    answer:
      "Bien sûr ! Nous pouvons fournir le code source et les fichiers de votre site Internet pour que vous puissiez le confier à un autre prestataire.",
  },
];

const questions = faq.map((question) => {
  return {
    "@type": "Question" as const,
    name: question.title,
    acceptedAnswer: {
      "@type": "Answer" as const,
      text: question.answer,
    },
  };
});

useJsonld(() => ({
  "@context": "https://schema.org",
  "@type": "FAQPage",
  mainEntity: questions,
}));

const questionOpened = ref();
function toggleQuestion(index: number) {
  if (questionOpened.value === index) {
    questionOpened.value = null;
  } else {
    questionOpened.value = index;
  }
}
</script>
<template>
  <section id="faq" class="faq">
    <div class="faq__headlines">
      <h1 class="faq__headlines__small">
        Questions courantes sur la creation de sites web
      </h1>
      <span class="faq__headlines__title">FAQ</span>
    </div>
    <div class="faq__cards">
      <div
        class="faq__cards__card"
        v-for="(question, index) in faq"
        :key="index"
        @click="toggleQuestion(index)"
      >
        <h2 class="faq__cards__card__question">
          <span class="icon"
            ><IconComponent
              :icon="questionOpened === index ? 'xx' : 'chat-circle-bold'"
              size="1rem"
              :color="colors['primary-color']"
          /></span>
          {{ question.title }}
        </h2>
        <p class="faq__cards__card__answer" v-if="questionOpened === index">
          {{ question.answer }}
        </p>
      </div>
    </div>
  </section>
</template>
<style lang="scss" scoped>
.faq {
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

  &__cards {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(288px, 1fr));
    align-items: flex-start;
    justify-content: center;
    gap: 2rem;
    width: 100%;

    @media (min-width: $big-tablet-screen) {
      grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
    }

    @media (min-width: $super-big-screen) {
      grid-template-columns: repeat(auto-fill, minmax(600px, 1fr));
    }

    &__card {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      width: 100%;
      gap: 1rem;
      cursor: pointer;
      height: fit-content;
      padding-top: 2rem;

      @media (min-width: $big-tablet-screen) {
        height: 100%;
      }

      &__question {
        display: flex;
        width: 100%;
        font-size: $text-size-3;
        font-weight: $regular;
        align-self: stretch;
        flex-direction: row;
        gap: 1rem;

        @media (min-width: $big-tablet-screen) {
          gap: 2rem;
        }

        .icon {
          width: 40px;
          height: 40px;
          background-color: $accent-color;
          display: flex;
          justify-content: center;
          align-items: center;
          border-radius: 2rem 2rem 2rem 0;
          margin-left: auto;
        }
      }

      &__answer {
        font-size: 1rem;
        font-weight: $regular;
        animation: fading 0.4s;
        width: 100%;
        line-height: 1.2rem;
      }

      &__link {
        animation: fading 0.4s;
        width: fit-content;
      }
    }
  }
}
</style>
