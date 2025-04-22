<template>
  <HeaderComponent />
  <MobileHeader />
  <main>
    <slot />
  </main>
  <FooterComponent />
</template>
<style lang="scss">
main {
  display: flex;
  flex-direction: column;
  min-height: 100dvh;
  margin: auto;
}
.v-enter-active,
.v-leave-active {
  transition: transform 0.3s linear;
  transform-origin: top right;
}

.v-enter-from,
.v-leave-to {
  transform: scale(0);
}
</style>
