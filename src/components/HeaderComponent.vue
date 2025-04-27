<script setup lang="ts">
import { onMounted, onUnmounted, watch } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
let header: HTMLElement | null = null;
let ticking = false;

function onScroll() {
  if (!header) return;
  if (!ticking) {
    window.requestAnimationFrame(() => {
      const add = window.scrollY > window.innerHeight;
      header!.classList.toggle("scrolled-vh", add);
      ticking = false;
    });
    ticking = true;
  }
}

function applyHeaderRule(path: string) {
  if (!header) return;

  window.removeEventListener("scroll", onScroll);

  const pathsWithBanner =
    path === "/" ||
    path === "/site-internet-entreprise" ||
    path === "/site-internet-sans-abonnement";

  if (pathsWithBanner) {
    header.classList.remove("scrolled-vh");
    window.addEventListener("scroll", onScroll, { passive: true });

    onScroll();
  } else {
    header.classList.add("scrolled-vh");
  }
}

onMounted(() => {
  header = document.querySelector("header");
  if (!header) return;
  applyHeaderRule(route.path);
});

watch(() => route.path, applyHeaderRule);

onUnmounted(() => window.removeEventListener("scroll", onScroll));
</script>
<template>
  <header class="header" ref="target">
    <NuxtLink to="/" class="logo noselect"
      ><img
        class="logo"
        src="@/assets/images/logotwf-light.svg"
        alt="logo tekila web factory"
    /></NuxtLink>
    <div class="header__shortcuts">
      <NuxtLink
        to="https://calendar.app.google/q4vewDNVHKHNjyDG6"
        target="_blank"
        ><PrimaryButton variant="secondary-color" icon="chat-circle-bold"
          >Prendre rendez-vous
        </PrimaryButton>
      </NuxtLink>
      <NuxtLink to="#why-choose-us" class="header__shortcuts__link"
        >Pourquoi nous choisir ?</NuxtLink
      >
    </div>
  </header>
</template>
<style lang="scss" scoped>
.logo {
  width: 100px;
}

.scrolled-vh {
  background-color: $accent-color;
}

.header {
  display: none;
  transition: background-color 0.2s linear;

  @media (min-width: $big-tablet-screen) {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem 4rem;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 2;
    width: 100%;
  }

  &__shortcuts {
    display: flex;
    gap: 1rem;
    align-items: center;

    &__link {
      color: $text-color-alt;
    }
  }

  &__nav {
    border: red solid 1px;

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
