<template>
  <section>
    <ul>
      <li v-for="(task, index) in tasks" class="shadow">
        <i type="button" class="task-check btn fas fa-check"></i>
        {{task}}
        <span type="button" v-on:click="removeTask(task, index)" class="task-remove btn">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>
  export default {
    name: "List",
    props: ['tasks',],
    methods: {
      removeTask(task, index) {
        this.$emit('task-delete', {task, index,});
      },
    },
  }
</script>

<style scoped lang="scss">

  $height: 50px;
  $border-radius: 5px;
  $gap-bottom: 10px;

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

      .btn {
        margin: 0 1rem; /* Single Responsibility Principle */
        &.task-check {
          line-height: $height;
          color: #62acde;
        }
        &.task-remove {
          margin-left: auto;
          color: red;
          color: #DE4343;
        }
      }
    }
  }
</style>
