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
      inputSearch: "",
      selectSearch: "",
    };
  },
};
</script>

<template>
  <div class="container-xl">
    <!-- Search-bar -->
    <div class="mt-5 mb-4">
      <div class="d-flex justify-content-center align-items-center">
        <div class="d-flex">
          <!-- Input Form -->
          <input
            class="form-control mx-2"
            type="text"
            placeholder="Select Character"
            aria-label=""
          />
          <!-- /Input Form -->
          <!-- SELECT -->
          <select class="form-select" aria-label="Default select example">
            <option selected>Select Status</option>
            <option value="1">Alive</option>
            <option value="2">Dead</option>
            <option value="3">Unknown</option>
          </select>
          <!-- /SELECT -->
        </div>
        <div class="">
          <div class="btn btn-info mx-2">Search</div>
          <div class="btn btn-warning">Reset</div>
        </div>
      </div>
    </div>
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
