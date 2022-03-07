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
      tasks: JSON.parse(localStorage.getItem('tasks') || '[]'),
    };
  },
  watch: {
    tasks: {
      handler(tasks) {
        localStorage.setItem('tasks', JSON.stringify(tasks));
      },
      deep: true,
    },
  },
  methods: {
    addTask(newTask, reset) {
      const value = newTask.trim();
      if (!value) {
        return;
      }
      const task = {
        id: +new Date(),
        checked: false,
        title: value,
      };
      //localStorage.setItem('tasks', JSON.stringify(task));
      this.tasks.push(task);
      reset();
    },
    deleteTask(task) {
      //const tasks = JSON.parse(localStorage.getItem('tasks'));
      //tasks.splice(this.tasks.indexOf(task), 1);
      this.tasks.splice(this.tasks.indexOf(task), 1);
    },
    clearTasks() {
      if (this.tasks.length === 0) return;
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
    display flex
    justify-content center

body
    background-color #f2f2f2
    width 100%
    height 100vh
    padding 3rem

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
