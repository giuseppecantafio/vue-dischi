<template>
  <div>
    <div class="card text-center my-2">
      <img
        :src="item.poster"
        class="card-img-top img-fluid my-4"
        :alt="item.author"
      />
      <h4>{{ item.title }}</h4>
      <p>{{ item.author }}<br />{{ item.year }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppCards",
  props: {
    item: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/general.scss";
.card {
  height: 270px;
  width: 150px;
  display: block !important;
  border-radius: 0 !important;
  background-color: $bg-cards;

  img {
    width: 100px;
    height: 100px;
    border-radius: 0 !important;
  }

  h4 {
    color: $primary;
    text-transform: uppercase;
    font-size: 1.2rem;
  }
  p {
    color: $secondary;
    font-size: 0.8rem;
  }
}
</style>
