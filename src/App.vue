<template>
  <AppHeaderVue />
  <main>
    <AppWelcome />
    <AppNavLinksVue />
  </main>
</template>

<script setup>
import AppWelcome from "./components/AppWelcome.vue";
import AppHeaderVue from "./components/AppHeader.vue";
import AppNavLinksVue from "./components/AppNavLinks.vue";
</script>

<style scoped lang="scss">
main {
  position: relative;
  top: -100px;
}
</style>
