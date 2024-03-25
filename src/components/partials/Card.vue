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
  <div class="col mb-3">
    <div class="card d-flex justify-content-center align-items-center">
      <img :src="image" :alt="name" class="mb-2" />
      <h4>{{ name }}</h4>
      <p>{{ status }}</p>
      <p>{{ species }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/scss/main.scss" as *;
.card {
  padding: 5px 10px;
  box-shadow: 0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0, 0, 0, 0);

  & img {
    width: 150px;
    aspect-ratio: 1;
    border-radius: 50%;
    box-shadow: 10px 10px 29px -21px rgba(0, 0, 0, 0.75);
  }
  p {
    margin-bottom: 10px;
  }
}
</style>
