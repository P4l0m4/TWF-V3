<script setup lang="ts">
import { ref, onMounted } from "vue";
import { colors } from "@/utils/colors";
import { onClickOutside } from "@vueuse/core";
import { useTemplateRef } from "vue";

const isMenuOpen = ref(false);

const target = useTemplateRef<HTMLElement>("target");
onClickOutside(target, () => (isMenuOpen.value = false));

onMounted(() => {
  const header = document.querySelector("header");
  if (!header) return;

  let ticking = false;

  function onScroll() {
    if (!ticking) {
      window.requestAnimationFrame(() => {
        if (!header) return;
        const scrolledPastVH = window.scrollY > window.innerHeight;
        header.classList.toggle("scrolled-vh", scrolledPastVH);
        ticking = false;
      });
      ticking = true;
    }
  }

  window.addEventListener("scroll", onScroll);
});
</script>
<template>
  <header class="header" ref="target">
    <NuxtLink to="/" class="logo noselect" @click="isMenuOpen = false"
      ><img
        class="logo"
        src="@/assets/images/logotwf-dark.svg"
        alt="logo tekila web factory"
    /></NuxtLink>
    <NuxtLink
      to="https://calendar.app.google/q4vewDNVHKHNjyDG6"
      target="_blank"
      style="margin-left: auto"
      ><PrimaryButton variant="secondary-color"
        >Prendre rendez-vous
      </PrimaryButton>
    </NuxtLink>
    <!-- <button
      type="button"
      class="menu-button noselect"
      @click="isMenuOpen = !isMenuOpen"
      aria-label="menu"
    >
      <IconComponent
        :icon="isMenuOpen ? 'xx' : 'list'"
        size="2rem"
        :color="colors['primary-color']"
      />
    </button> -->
    <!-- <Transition>
      <nav class="header__nav" v-if="isMenuOpen">
        <ul class="header__nav__links">
          <li class="header__nav__links__link">
            <NuxtLink
              to="/contact-ebeniste-savoie"
              class="nuxt-link"
              style="text-decoration: underline"
              exact
              >Devis et contact<span class="line"></span
            ></NuxtLink>
          </li>
        </ul>
      </nav>
    </Transition> -->
  </header>
</template>
<style lang="scss" scoped>
.logo {
  width: 100px;
}
.scrolled-vh {
  display: flex !important;
  background-color: $accent-color;
}
.header {
  display: none;
  position: relative;
  padding: 1.5rem;
  background-color: $base-color;
  box-shadow: $shadow;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 2;

  &__nav {
    position: fixed;
    top: 0.75rem;
    right: 1rem;
    z-index: 2;

    &__links {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      background-color: $secondary-color;
      padding: 1rem;
    }
  }

  .menu-button {
    position: fixed;
    right: 1rem;
    top: 0.75rem;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50px;
    height: 50px;
    background-color: $secondary-color;
    z-index: 1;
    border-radius: 0;
  }
}

.nuxt-link {
  text-decoration: none;
  color: $text-color-alt;
  white-space: nowrap;
  display: flex;
  flex-direction: column;
  gap: 2px;

  .line {
    width: 0px;
    height: 2px;
    background-color: transparent;
    transition: width 0.3s ease, background-color 0.3s ease;
  }
}

.router-link-exact-active {
  .line {
    width: 100%;
    background-color: $accent-color;
  }
}
</style>
