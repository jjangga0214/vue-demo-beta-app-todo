<template>
  <div class="input-box shadow">
    <input type="text" v-model="newTask" v-on:keyup.enter="addTask" placeholder="입력해주세요">
    <span v-on:click="addTask" class="add btn add-btn" type="button">
      <i class="fas fa-plus add btn add-label" aria-hidden="true"></i>
    </span>
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
  $height: 50px;
  $border-radius: 5px;
  $add-width: 3rem;
  .input-box {
    background: white;
    height: $height;
    line-height: $height;
    border-radius: $border-radius;
    input {
      float: left;
      margin-left: 1rem;
      line-height: $height;
      border-style: none;
      font-size: 1.3rem;
      background-color: transparent;
      width: calc(100% - (#{$add-width} + 1rem  + 1rem));
      /*
      100% - (#{$add-width} + 1rem) = add-btn 과 딱 맞는다.
      왜냐하면 100% - margin-left(1rem) 에서 add-btn의 너비인 #{$add-width} 을 뺀 것이기 때문이다.
      add-btn 과 여유를 두기 위해 거기서 1rem 을 또 뺀다.
      */
      &:focus {
        outline: none;
      }
    }
    .add {
      cursor: pointer;
      &.add-btn {
        float: right;
        background: linear-gradient(to right, #6478FB, #8768FB);
        display: inline-block;
        width: $add-width;
        border-radius: 0 $border-radius $border-radius 0;
      }
      &.add-label {
        color: white;
        /*vertical-align: middle;*/
      }
    }

  }
</style>
