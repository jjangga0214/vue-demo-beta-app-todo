<template>
  <div id="app">
    <!--
    component 는 root 가 필요하다
    -->
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter' // import 에서 .vue 는 생략가능하다.

  export default {
    components: {
      TodoHeader,
      TodoInput,
      TodoList,
      TodoFooter,
    }
  }
</script>

<style lang="scss">

</style>
