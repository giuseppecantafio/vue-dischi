<template>
  <div>
    <header class="d-flex align-items-center ">
      <img src="../assets/logo.png" alt="Logo" class="mx-2">
    </header>
  </div>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>

<style lang="scss" scoped>
@import "@/style/general.scss";
header {
  height: 50px;
  width: 100%;
  background-color: $bg-header;
  img{
    width: 30px;
    height: 30px;
  }
}
</style>
