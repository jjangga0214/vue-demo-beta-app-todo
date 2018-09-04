<template>
  <div>
    <span>{{mark}}</span>

    <div class="input-box shadow">
      <input type="text" v-model="newTask" v-on:keyup.enter="addTask" placeholder="입력해주세요">
      <span v-on:click="addTask" class="add add-btn">
      <i class="fas fa-plus" aria-hidden="true"></i>
      <i class="add add-label">추가</i>
    </span>
    </div>
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
  input:focus {
    outline: none;
  }

  $input-box-height: 50px;
  $border-radius: 5px;
  $add-width: 3rem; 
  .input-box {
    background: white;
    height: $input-box-height;
    line-height: $input-box-height;
    border-radius: $border-radius;
    input {
      float: left;
      margin-left: 1rem;
      line-height: $input-box-height;
      border-style: none;
      font-size: 1.3rem;
      background-color: transparent;
      width: calc(100% - (#{$add-width} + 2rem));
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
