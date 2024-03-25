<script>
import Card from "./partials/Card.vue";
import { store } from "../data/store";

export default {
  components: {
    Card,
  },

  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container-xl">
    <div class="row row-cols-3 mt-3">
      <Card
        v-for="item in this.store.cardList"
        :key="item.id"
        :image="item.image"
        :name="item.name"
        :status="item.status"
        :species="item.species"
      />
    </div>
  </div>
</template>

<style lang="scss">
@use "../assets/scss/main.scss" as *;
</style>
