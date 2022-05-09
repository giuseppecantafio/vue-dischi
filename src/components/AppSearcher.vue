<template>
  <div class="pb-1">
    <select class="form-select" v-model="inputText" @change="getChanged">
      <option  selected value="all">Tutto</option>
      <option :value="item" v-for="(item, index) in genere" :key="index">
        {{ item }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "AppSearcher",
  props: {
    genere: Array,
  },
  data() {
    return {
      inputText: "",
    };
  },
  methods: {
    getChanged() {
      this.$emit("performChange", this.inputText);
    },
  },
};
</script>

<style lang="scss" scoped></style>
