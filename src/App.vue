<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

import { store } from "./data/store";

export default {
  components: {
    Header,
    Main,
  },
  data() {
    return {
      axios,
      store,
      myArray: [1, 2, 3],
    };
  },

  methods: {
    getApi() {
      axios
        .get(this.store.apiUrl, {})
        // prendo i risultati della richiesta API
        .then((result) => {
          result.data.results.forEach((element, index) => {
            this.store.cardList.push(element);
            console.log("loop ----> ", index);
          });
          // this.store.cardList = result.data.results;
          console.log(this.store.cardList);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },

  mounted() {
    this.getApi();
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
