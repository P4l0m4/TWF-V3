<template>
  <section class="question">
    <h2 class="question__title">
      Des questions sur les sites Internet ou sur nos prestations ?
    </h2>
    <span class="question__subtitle">
      Consultez notre
      <NuxtLink
        to="/questions-courantes-sur-la-creation-de-sites-web"
        style="text-decoration: underline"
        >foire aux questions</NuxtLink
      ></span
    >
  </section>
</template>
<style lang="scss" scoped>
.question {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 2rem 1rem;
  width: 100%;

  @media (min-width: $big-tablet-screen) {
    padding: 4rem;
  }

  &__title {
    font-size: $subtitles-size-1;
    font-weight: $regular;

    @media (min-width: $big-tablet-screen) {
      font-size: $subtitles-size-2;
    }
  }

  &__subtitle {
    font-size: $subtitles-size-2;
    width: 100%;
    text-wrap: balance;

    @media (min-width: $big-tablet-screen) {
      font-size: $titles-size-1;
    }
  }
}
</style>
