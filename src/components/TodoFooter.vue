<template>
  <div class="tasks-clear btn shadow" type="button" v-on:click="$emit('tasks-clear')">Clear All</div>
</template>

<script>
  export default {
    name: "TodoFooter",
  }
</script>

<style scoped lang="scss">
  $height: 50px;
  .btn.tasks-clear {
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
