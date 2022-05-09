<template>
  <main>
    <div class="wrapper">
      <div class="container pt-3">
        <app-searcher @performChange="mySearch($event)" :genere="genre" />
        <div class="row row-cols-5">
          <div class="col" v-for="card in filteredSongs" :key="card.author">
            <app-cards :item="card" />
          </div>
        </div>
      </div>
      <app-loader v-if="loading" />
    </div>
  </main>
</template>

<script>
import AppCards from "./AppCards.vue";
import axios from "axios";
import AppLoader from "./AppLoader.vue";
import AppSearcher from "./AppSearcher.vue";

export default {
  components: { AppCards, AppLoader, AppSearcher },
  name: "AppMain",
  data() {
    return {
      cards: [],
      genre: [],
      loading: true,
      searchText: "",
    };
  },
  mounted() {
    this.loading = true;
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        this.cards = res.data.response;
        this.cards.forEach((card) => {
          if (!this.genre.includes(card.genre)) {
            this.genre.push(card.genre);
          }
        });
      })
      .catch((error) => {
        console.log(error);
      })
      .finally(() => {
        this.loading = false;
        console.log(this.genre);
      });
  },
  methods: {
    mySearch(text) {
      this.searchText = text;
    },
  },
  computed: {
    filteredSongs() {
      if (this.searchText === "") {
        return this.cards;
      }
      return this.cards.filter((element) => {
        return element.genre === this.searchText;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/general.scss";
main {
  height: calc(100vh - 50px);
  width: 100%;
  background-color: $bg-main;
  .wrapper {
    width: 70%;
    margin: 0 auto;
  }
}
</style>
