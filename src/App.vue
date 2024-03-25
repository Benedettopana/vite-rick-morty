<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  components: {
    Header,
    Main,
  },
  data() {
    return {
      axios,
    };
  },
};
</script>

<template>
  <div>
    <div class="text-danger">Bootstrap</div>
  </div>
</template>

<style lang="scss">
@import "./assets/scss/main.scss";
</style>
