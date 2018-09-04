<template>
  <div>
    <span>{{mark}}</span>
    <br>
    <input type="text" v-model="newTask" placeholder="입력해주세요">
    <button v-on:click="addTask">추가</button>
  </div>
</template>

<script>
  export default {
    name: "Input",
    data() {
      return {
        newTask: '',
      };
    },
    methods: {
      addTask() {
        const key = this.newTask.trim();
        if (key) {
          console.log(key + " : " + this.mark);
          localStorage.setItem(key, this.mark);
        }
        this.clearInput();
      },
      clearInput() {
        this.newTask = '';
      },
    },
    computed: {
      mark() {
        return this.newTask + '!';
      },
    },
  }
</script>

<style scoped lang="scss">

</style>
