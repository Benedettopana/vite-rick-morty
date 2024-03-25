<script>
export default {
  props: {
    image: String,
    name: String,
    status: String,
    species: String,
  },
};
</script>

<template>
  <div class="col mb-2">
    <div class="card d-flex justify-content-center align-items-center">
      <img :src="image" :alt="name" class="mb-2" />
      <p>{{ name }}</p>
      <p>{{ status }}</p>
      <p>{{ species }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/scss/main.scss";
.card {
  padding: 5px 10px;
  & img {
    width: 150px;
    aspect-ratio: 1;
    border-radius: 50%;
  }
  p {
    margin-bottom: 10px;
  }
}
</style>
