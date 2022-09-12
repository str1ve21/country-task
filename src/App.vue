<template>
  <AppHeader />
  <main>
    <AppWelcome />
    <AppNavLinks />
    <AppAbout />
    <AppCards />
    <AppGallery />
    <AppReviews />
  </main>
  <AppFooter />
</template>

<script setup>
import AppWelcome from "./components/AppWelcome.vue";
import AppHeader from "./components/AppHeader.vue";
import AppNavLinks from "./components/AppNavLinks.vue";
import AppAbout from "./components/AppAbout.vue";
import AppCards from "./components/AppCards.vue";
import AppGallery from "./components/AppGallery.vue";
import AppReviews from "./components/AppReviews.vue";
import AppFooter from "./components/AppFooter.vue";
</script>

<style scoped lang="scss">
main {
  position: relative;
}
</style>
