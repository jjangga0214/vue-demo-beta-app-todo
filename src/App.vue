<template>
  <div id="app" class="app">
    <!--
    component 는 root 가 필요하다
    -->
    <TodoHeader></TodoHeader>
    <TodoInput v-on:task-create="createTask"></TodoInput>
    <TodoList v-bind:tasks="rawTasks" v-on:task-delete="deleteTask"></TodoList>
    <TodoFooter v-on:tasks-clear="clearTasks"></TodoFooter>
  </div>
</template>

<script>
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter' // import 에서 .vue 는 생략가능하다.

  export default {
    data() {
      return {
        tasks: [],
      };

    },
    computed: {
      rawTasks() {
        return this.tasks.map(el => el.value);
      },

    },
    methods: {
      markTask(rawTask) {
        return rawTask + '!';
      },
      unmarkTask(task) {
        return task.replace(/.$/, "");
      },
      createTask(rawTask) {
        if (this.tasks.findIndex(el => el.key == rawTask) != -1) {
          return;
        }
        const taskMarked = this.markTask(rawTask);
        this.tasks.push({
          key: rawTask,
          value: taskMarked,
        });
        localStorage.setItem(rawTask, taskMarked);
        this.tasks.sort((a, b) => a.key.localeCompare(b.key));
      },
      deleteTask(data) {
        this.tasks.splice(data.index, 1);
        localStorage.removeItem(this.unmarkTask(data.task));
      },
      clearTasks() {
        this.tasks = [];
        localStorage.clear();
      },
    },
    created() {
      for (let i = 0; i < localStorage.length; i++) {
        const key = localStorage.key(i);
        this.tasks.push({
          key,
          value: localStorage.getItem(key),
        });
      }
    },
    components: {
      TodoHeader,
      TodoInput,
      TodoList,
      TodoFooter,
    }
  }
</script>

<style lang="scss">
  $max-width: 894px;
  body {
    text-align: center;
    font-family: 'Source Sans Pro', sans-serif;
    background-color: #F6F6F8;
    .app { /* id 는 너무 강력하므로 overriding 이 용이한 class 를 사용한다. */
      max-width: $max-width;
      margin: 0 auto 0;

      button {
        border-style: groove;
      }
      .shadow {
        box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.05);
      }
      .btn, *[type=button] {
        cursor: pointer;
      }
    }
  }
</style>
