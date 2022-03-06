<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  components: {
    Header,
    Main,
  },
  data() {
    return {
      tasks: [
        { id: 1, checked: false, title: 'TASK 1' },
        { id: 2, checked: false, title: 'TASK 2' },
      ],
    };
  },
  methods: {
    addTask(newTask, reset) {
      const value = newTask.trim();
      if (!value) {
        return;
      }
      this.tasks.push({
        id: +new Date(),
        checked: false,
        title: value,
      });
      reset();
    },
    deleteTask(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    },
    clearTasks() {
      this.tasks = this.tasks.filter((t) => t.checked === false);
    },
  },
};
</script>

<template>
  <h1>TODO APP - VUE</h1>
  <Header :tasks="tasks" :addTask="addTask" />
  <Main :tasks="tasks" :deleteTask="deleteTask" :clearTasks="clearTasks" />
</template>

<style lang="stylus">
html
    font-family Ubuntu
    width 100%
    height 100vh
    display flex
    justify-content center

body
    background-color #f2f2f2

.container
    display flex
    flex-direction column
    justify-content center
    align-items center

.section
    margin 2rem

h1
    color #1592ab

::selection
    background transparent
</style>
