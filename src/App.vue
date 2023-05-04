<template>
  <HomeView id="app"></HomeView>
</template>

<script>
import HomeView from "./components/HomeView.vue";

export default {
  name: "App",
  components: {
    HomeView,
  },
};
</script>

<style>
body{
  background: #F7F6F4;
  margin: 0;
  height: 100vh;
  width: 100vw;
}
#app {
  font-family: "PT Sans";
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 150%;
  max-width: 1920px;
}
</style>
