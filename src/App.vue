<template>
  <div>
    <Header />
    <MainPage />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import MainPage from "./components/MainPage.vue";

export default {
  name: "App",
  components: {
    MainPage,
    Header,
  },
};
</script>

<style lang="scss">
$maxWidthContainer: 1250px;

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  .container {
    max-width: $maxWidthContainer;
    height: 100%;
    margin: 0 auto;
    padding: 0 15px;
  }
}
</style>
