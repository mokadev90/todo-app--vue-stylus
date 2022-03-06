<script>
export default {
  data() {
    return {
      newTask: '',
    };
  },
  props: {
    tasks: Array,
    addTask: Function,
  },
  methods: {
    reset() {
      this.newTask = '';
    },
  },
};
</script>

<template>
  <div class="section flex">
    <div class="box">
      <input type="text" v-model="newTask" />
    </div>
    <button class="box-btn" @click="addTask(newTask, reset)">
      <svg
        width="25"
        height="24"
        viewBox="0 0 25 24"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M15.0586 2.013H9.05859V9H2.05859V15H9.05859V21.987H15.0586V15H22.0586V9H15.0586V2.013Z"
          fill="black"
        />
      </svg>
    </button>
  </div>
</template>

<style lang="stylus" scoped>

.flex
    display flex
    justify-content center
    align-items center

.box
    width 18rem
    height 2rem
    background-color #c5c5c5
    padding 1rem
    border-radius 8px

.box-btn
    background-color #c5c5c5
    border none
    width 2rem
    height 2rem
    border-radius 8px
    margin .5rem
    display flex
    justify-content center
    align-items center

    path
        fill #1592ab

input
    border none
    border-radius 4px
    height 100%
    width 100%
    padding 0
    font-family Ubuntu
    font-size 1.5rem
</style>
