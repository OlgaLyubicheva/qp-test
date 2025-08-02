<script setup>
  import TheHeader from "./components/TheHeader.vue";
  import TheFooter from "./components/TheFooter.vue";
  import HomeView from "./views/HomeView.vue";
</script>

<template>
  <TheHeader></TheHeader>
  <HomeView/>
  <TheFooter></TheFooter>
</template>

<style lang="scss">
@import "./assets/styles/_vars.scss";
#app {
  background: #ffffff;
  font-family: $font-prime;
  font-weight: 400;
  font-style: normal;
  color: $text-light;
  font-size: 16px;
}
</style>
