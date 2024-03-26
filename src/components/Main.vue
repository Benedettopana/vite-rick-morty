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

  computed: {
    filteredCharacters() {
      if (!this.inputSearch) {
        // Se inputSearch è vuoto, restituisci l'intera lista di personaggi
        return this.store.cardList;
      } else {
        // Altrimenti, filtra la lista di personaggi in base all'input di ricerca
        const searchQuery = this.inputSearch.toLowerCase();
        return this.store.cardList.filter((character) =>
          character.name.toLowerCase().includes(searchQuery)
        );
      }
    },
  },
};
</script>

<template>
  <div class="container-xl">
    <div class="row row-cols-3 mt-3">
      <Card
        v-for="item in filteredCharacters"
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
