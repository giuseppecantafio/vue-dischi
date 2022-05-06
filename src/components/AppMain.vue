<template>
  <main>
    <div class="wrapper">
        <div class="container pt-3">
          <div class="row row-cols-5">
            <div class="col" v-for="card in cards" :key="card.author">
              <app-cards :item="card" />
            </div>
          </div>
        </div>
    </div>
  </main>
</template>

<script>
import AppCards from "./AppCards.vue";
import axios from "axios";

export default {
  components: { AppCards },
  name: "AppMain",
  data() {
    return {
      cards: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        this.cards = res.data.response;
        console.log(this.cards);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/general.scss";
main {
  height: calc(100vh - 50px);
  width: 100%;
  background-color: $bg-main;
  .wrapper{
      width: 70%;
      margin: 0 auto;
  }
}
</style>
