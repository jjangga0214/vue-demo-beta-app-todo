<template>
  <section>
    <transition-group name="task-list" tag="ul">
      <li v-for="(task, index) in tasks" v-bind:key="task" class="shadow">
        <i type="button" class="task-check btn fas fa-check"></i>
        {{task}}
        <span type="button" v-on:click="deleteTask(task, index)" class="task-delete btn">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>

  </section>
</template>

<script>
  export default {
    name: "TodoList",
    props: ['tasks',],
    methods: {
      deleteTask(task, index) {
        this.$emit('task-delete', {task, index,});
      },
    },
  }
</script>

<style scoped lang="scss">

  $height: 50px;
  $border-radius: 5px;
  $gap-bottom: 10px;

  /*.task-list-move {
    transition: transform 1s;
  }*/

  ul {
    padding: 0;
    list-style: none;
    text-align: left;
    margin-top: $gap-bottom;

    li {
      background-color: white;
      margin-bottom: $gap-bottom;
      /*
      * width: 100%; 는 padding 을 제외하고 계산하기 때문에 꼭 부모의 너비와 같은 것은 아니다.
      * 따라서 width : auto; 를 사용한다.
      */
      width: auto;
      display: flex;
      min-height: $height;
      height: $height;
      line-height: $height;
      border-radius: $border-radius;

      &.task-list-enter-active {
        transition: all .5s;
      }

      &.task-list-leave-active {
        transition: all .3s;
      }

      &.task-list-enter, &.task-list-leave-to {
        //transform: scaleX(0.95);
        opacity: 0;
        transform: translateX(10px);
      }

      .btn {
        margin: 0 1rem; /* Single Responsibility Principle */
        &.task-check {
          line-height: $height;
          color: #62acde;
        }
        &.task-delete {
          margin-left: auto;
          color: red;
          color: #DE4343;
        }
      }
    }
  }
</style>
