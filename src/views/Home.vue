<template>
  <div class="home">
    <router-link to="/quickStart" class="nav-item">QuickStart</router-link>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
}
</script>

<style scoped lang="scss">
.home {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  .nav-item {
    margin: 10px;
  }
}
</style>
