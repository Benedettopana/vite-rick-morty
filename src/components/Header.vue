<script>
import axios from "axios";
import { store } from "../data/store";

export default {
  // emits: ["search-results"],
  emits: ["search-results-updated"],
  data() {
    return {
      store,
      searchQuery: "",
    };
  },

  methods: {
    searchCharacter() {
      this.store.searchResults = [];
      axios
        .get(`${this.store.apiName}${this.searchQuery}`)
        .then((response) => {
          // Aggiorno il risultato della ricerca
          store.searchResults = response.data.results;
          // Parte l'evento in ascolto dal main per la visualizzazione dei risultati
          this.$emit("search-results-updated");
        })
        .catch((error) => {
          console.error(error);
        });
    },

    resetSearch() {
      // Resetto le var di ricerca
      this.searchQuery = "";
      store.searchResults = [];
    },
  },

  computed: {
    searchResults() {
      return this.store.searchResults;
    },
  },
};
</script>

<template>
  <div>
    <h1 class="text-center m-3">{{ this.store.mainTitle }}</h1>
  </div>
  <!-- Search-bar -->
  <div class="mt-5 mb-5">
    <div class="d-flex justify-content-center align-items-center">
      <div class="d-flex">
        <!-- Input Form -->
        <input
          class="form-control mx-2"
          type="text"
          placeholder="Select Character"
          v-model="searchQuery"
          @input="searchCharacter"
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
        <div class="btn btn-info mx-2" @click="searchCharacter">Search</div>
        <div class="btn btn-warning" @click="resetSearch">Reset</div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@use "../assets/scss/main.scss" as *;
</style>
