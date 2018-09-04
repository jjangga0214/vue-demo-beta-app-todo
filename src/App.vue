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
  body {
    text-align: center;
    font-family: 'Source Sans Pro', sans-serif;
    background-color: #F6F6F8;
    input {
      border-style: groove;
    }
    button {
      border-style: groove;
    }
    .shadow {
      box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.05);
    }
  }
</style>
