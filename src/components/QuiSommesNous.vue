<template>
  <section id="who-we-are" class="qui-sommes-nous">
    <div class="qui-sommes-nous__wrapper">
      <h2 class="qui-sommes-nous__wrapper__title">Qui sommes nous ?</h2>

      <p class="qui-sommes-nous__wrapper__paragraph">
        Tekila Web Factory, c'est avant tout une
        <span class="line-through">petite entreprise locale</span>. <br /><br />
        Nous créons vos sites Internet depuis Chambéry, en Savoie. Nous sommes
        une équipe technique et créative avec un faible pour le fromage, la
        charcuterie et le Web.<br /><br />
        Ce qu'on aime aussi, c'est voir nos clients hyper satisfaits, et la
        sensation merveilleuse d'avoir fait une vraie différence pour leur
        entreprise.
        <br /><br />
        C'est pour ça qu'on met toujours le paquet sur le
        <span class="line-through">service client</span>. Notre meilleure
        publicité, c'est quand vous réussissez !
      </p>
    </div>
    <span class="qui-sommes-nous__image"></span>
  </section>
</template>
<style scoped lang="scss">
.qui-sommes-nous {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 2rem 1rem;
  width: 100%;

  @media (min-width: $big-tablet-screen) {
    gap: 4rem;
    padding: 4rem;
    flex-direction: row;
  }

  &__wrapper {
    display: flex;
    gap: 2rem;
    flex-direction: column;

    @media (min-width: $big-tablet-screen) {
      gap: 4rem;
    }

    &__title {
      font-size: $subtitles-size-1;
      font-weight: $regular;

      @media (min-width: $big-tablet-screen) {
        font-size: $subtitles-size-2;
      }
    }

    &__paragraph {
      font-size: $text-size-2;
      width: 100%;

      @media (min-width: $big-tablet-screen) {
        min-width: 400px;
      }

      .line-through {
        position: relative;

        &::before {
          content: "";
          display: block;
          background-color: $accent-color;
          opacity: 0.25;
          width: 100%;
          height: 1rem;
          z-index: -1;
          position: absolute;
          transform: rotate(-3deg);
          inset: 0;
          top: 0.25rem;
        }
      }
    }
  }

  &__image {
    max-width: 600px;
    width: 100%;
    min-width: 300px;
    height: 500px;
    background-position: center;
    background-size: cover;
    border-radius: 0 30%;
    background-image: url("@/assets/images/curiosity.webp");
  }
}
</style>
