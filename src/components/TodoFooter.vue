<template>
  <div class="btn clear-btn shadow" type="button" v-on:click="clear">Clear All</div>
</template>

<script>
  export default {
    name: "Footer",
    methods: {
      clear() {
        console.log('clear');
        localStorage.clear()
      }
    }
  }
</script>

<style scoped lang="scss">
  $height: 50px;
  * {
    color: red;
    color: #E20303;
    background-color: white;
    height: $height;
    line-height: $height;
    max-width: 200px;
    margin: 0 auto;
    border-radius: $height * 0.1;

  }
</style>
