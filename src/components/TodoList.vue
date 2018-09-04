<template>
  <section>
    <ul>
      <li v-for="task in tasks">{{task}}</li>
    </ul>
  </section>
</template>

<script>
  export default {
    name: "List",
    data() {
      return {
        tasks: [],
      };
    },
    created() {
      for (let i = 0; i < localStorage.length; i++) {
        this.tasks.push(localStorage.getItem(localStorage.key(i)))
      }
    },
  }
</script>

<style scoped lang="scss">

</style>
