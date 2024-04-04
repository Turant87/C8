<template>
 <div id="app">
  <MyShop shop-title="Магазин Один" />
  <MyShop shop-title="Магазин Два" />
 </div>
</template>

<script>
  import MyShop from "@/components/MyShop.vue";
  export default {
    components:{
      MyShop
    }
  }
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
