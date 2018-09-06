<template>
  <div>
    <div class="input-box shadow">
      <input type="text" v-model="newTask" v-on:keyup.enter="createTask" placeholder="입력해주세요">
      <span v-on:click="createTask" class="task-create btn" type="button">
      <i class="task-create label fas fa-plus" aria-hidden="true"></i>
    </span>
    </div>
    <Modal v-show="warn" v-on:close="warn = false">
      <h3 slot="header">경고</h3>
      <div slot="body">할 일을 입력해주세요</div>
      <div slot="footer">
        <button class="btn task-create-warn-accept modal-default-button" v-on:click="warn  = false">
          OK
        </button>
      </div>
    </Modal>
  </div>
</template>

<script>
  import Modal from './common/Modal.vue'

  export default {
    name: "Input",
    data() {
      return {
        newTask: '',
        warn: false,
      };
    },
    components: {
      Modal,
    },
    methods: {
      createTask() {
        this.newTask = this.newTask.trim();
        if (this.newTask) {
          this.$emit('task-create', this.newTask);
        } else {
          this.warn = true;
          setTimeout(() => this.warn = false, 2000); // es6 fat arrow lambda 는 외부 scope 가 capture 된다.
        }
        this.clearInput();
      },
      clearInput() {
        this.newTask = '';
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
      width: calc(100% - (#{$add-width} + 1rem + 1rem));
      /*
      100% - (#{$add-width} + 1rem) = add-btn 과 딱 맞는다.
      왜냐하면 100% - margin-left(1rem) 에서 add-btn의 너비인 #{$add-width} 을 뺀 것이기 때문이다.
      add-btn 과 여유를 두기 위해 거기서 1rem 을 또 뺀다.
      */
      &:focus {
        outline: none;
      }
    }
    .btn {
      cursor: pointer;
      &.task-create {
        float: right;
        background: linear-gradient(to right, #6478FB, #8768FB);
        display: inline-block;
        width: $add-width;
        border-radius: 0 $border-radius $border-radius 0;
      }
      &.task-create-warn-accept {
        background-color: white;
      }
    }
    .label {
      &.task-create {
        color: white;
        /*vertical-align: middle;*/
      }
    }

  }
</style>
