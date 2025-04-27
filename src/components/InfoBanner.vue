<script setup lang="ts">
import { colors } from "@/utils/colors";
</script>
<template>
  <section class="info-mini-banner">
    <p class="info-mini-banner__headline">
      A la recherche d’un prestataire sérieux pour créer un site internet ?
    </p>

    <div class="info-mini-banner__info">
      <span class="info-mini-banner__info__contact-me">
        <IconComponent
          icon="phone"
          size="1.25rem"
          :color="colors['text-color']"
        />Appelez nous</span
      >
      <a href="tel:0623041637" class="info-mini-banner__info__tel"
        >06 95 15 53 01</a
      >

      <PrimaryButton variant="accent-color"
        >Prenez rendez-vous avec nous</PrimaryButton
      >
    </div>
  </section>
</template>
<style lang="scss" scoped>
.info-mini-banner {
  display: flex;
  gap: 2rem;
  background-color: $accent-color;
  flex-direction: column;

  @media (min-width: $big-tablet-screen) {
    justify-content: space-between;
    flex-direction: row;
    align-items: center;
    height: 303px;
  }

  @media (min-width: $laptop-screen) {
    gap: 4rem;
  }

  &__headline {
    font-size: $titles-size-1;
    color: $primary-color;
    font-weight: $bold;
    text-wrap: balance;
    max-width: 1000px;
    padding: 2rem;

    @media (min-width: $laptop-screen) {
      font-size: 3rem;
      padding: 4rem;
      padding-right: 0rem;
      font-size: $titles-size-2;
    }
  }

  &__info {
    display: flex;
    gap: 1rem;
    flex-direction: column;
    align-items: end;
    background-color: $primary-color;
    padding: 2rem;
    height: 100%;

    @media (min-width: $big-tablet-screen) {
      width: fit-content;
      border-radius: 0 130px 0 130px;
      position: relative;
      gap: 2rem;
      padding: 4rem;

      &::before {
        content: "";
        display: block;
        position: absolute;
        top: 0;
        left: -100px;
        width: 100px;
        height: 100px;
        background-color: $accent-color;
        border-radius: 0 130px 0 0;
        z-index: 1;
      }

      &::after {
        content: "";
        display: block;
        position: absolute;
        top: 0;
        left: -100px;
        width: 100px;
        height: 100px;
        background-color: $primary-color;
      }
    }

    @media (min-width: $laptop-screen) {
      flex-direction: column;
    }

    &__contact-me {
      font-size: $text-size-3;
      color: $text-color;
      font-weight: $regular;
      display: flex;
      gap: 0.5rem;
      align-items: center;
      width: fit-content;
    }

    &__tel {
      font-size: $subtitles-size-1;
      color: $text-color;
      font-weight: $bold;
      display: flex;
      gap: 1rem;
      align-items: center;
      white-space: nowrap;

      @media (min-width: $desktop-screen) {
        font-size: $subtitles-size-2;
      }
    }
  }
}
</style>
