<script>
import { store } from "../data/store";
export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div>
    <h1 class="text-center m-3">{{ this.store.mainTitle }}</h1>
  </div>
</template>

<style lang="scss" scoped></style>
