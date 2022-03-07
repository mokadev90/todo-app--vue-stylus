<script>
export default {
  data() {
    return {
      filter: 'All', //All, Checked, Unchecked
    };
  },
  props: {
    tasks: Array,
    deleteTask: Function,
    clearTasks: Function,
  },
  computed: {
    tasksLeft() {
      const left = this.tasks.length
        ? this.tasks.filter((t) => t.checked === false).length || 0
        : 0;
      return left;
    },
  },
};
</script>
<template>
  <div class="section flex">
    <div v-for="task in tasks" :key="task.id">
      <div
        class="item"
        v-if="
          filter === 'All' ||
          (filter === 'Checked' && task.checked === true) ||
          (filter === 'Unchecked' && task.checked === false)
        "
      >
        <div
          v-if="!task.checked"
          @click="task.checked = !task.checked"
          class="box-btn"
        >
          <svg
            width="24"
            height="25"
            viewBox="0 0 24 25"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M7 5.5C5.897 5.5 5 6.397 5 7.5V17.5C5 18.603 5.897 19.5 7 19.5H17C18.103 19.5 19 18.603 19 17.5V7.5C19 6.397 18.103 5.5 17 5.5H7ZM7 17.5V7.5H17L17.002 17.5H7Z"
              fill="black"
            />
          </svg>
        </div>
        <div v-else class="box-btn" @click="task.checked = !task.checked">
          <svg
            width="24"
            height="25"
            viewBox="0 0 24 25"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M7 5.5C6.46957 5.5 5.96086 5.71071 5.58579 6.08579C5.21071 6.46086 5 6.96957 5 7.5V17.5C5 18.0304 5.21071 18.5391 5.58579 18.9142C5.96086 19.2893 6.46957 19.5 7 19.5H17C17.5304 19.5 18.0391 19.2893 18.4142 18.9142C18.7893 18.5391 19 18.0304 19 17.5V7.5C19 6.96957 18.7893 6.46086 18.4142 6.08579C18.0391 5.71071 17.5304 5.5 17 5.5H7ZM11 15.914L8.293 13.207L9.707 11.793L11 13.086L14.793 9.293L16.207 10.707L11 15.914Z"
              fill="black"
            />
          </svg>
        </div>
        <label type="text" class="box" :class="{ checked: task.checked }">{{
          task.title
        }}</label>
        <div class="box-btn" @click="deleteTask(task)">
          <svg
            width="24"
            height="25"
            viewBox="0 0 24 25"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M6 7.5H5V20.5C5 21.0304 5.21071 21.5391 5.58579 21.9142C5.96086 22.2893 6.46957 22.5 7 22.5H17C17.5304 22.5 18.0391 22.2893 18.4142 21.9142C18.7893 21.5391 19 21.0304 19 20.5V7.5H6ZM10 19.5H8V10.5H10V19.5ZM16 19.5H14V10.5H16V19.5ZM16.618 4.5L15 2.5H9L7.382 4.5H3V6.5H21V4.5H16.618Z"
              fill="black"
            />
          </svg>
        </div>
      </div>
    </div>
  </div>
  <div class="section">
    <div class="texts">
      <h3 class="top">{{ tasksLeft }} left</h3>
      <h3 class="top" @click="clearTasks()">Clear completed</h3>
    </div>
    <div class="btns">
      <button class="box-btn-foot" @click="filter = 'All'">All</button>
      <button class="box-btn-foot" @click="filter = 'Unchecked'">Active</button>
      <button class="box-btn-foot" @click="filter = 'Checked'">Done</button>
    </div>
  </div>
  <span class="author">by MOKA</span>
</template>

<style lang="stylus" scoped>
.flex
    display flex
    justify-content center
    align-items center
    flex-direction column

.item
    display flex
    justify-content center
    align-items center
    margin-bottom 1rem

.box
    width 15rem
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

    button
        border none
        padding 1
.checked
    font-style italic
    text-decoration line-through
label
    border none
    border-radius 4px
    height 100%
    width 100%
    padding 0
    font-family Ubuntu
    font-size 1.5rem


.flex
    display flex
    justify-content center
    align-items center
    width 100%
    justify-content space-between

.top
    margin-top 0

.texts
    display flex
    justify-content space-between

.btns
    display flex


.box-btn-foot
    background-color #c5c5c5
    border none
    width 5rem
    height 3rem
    border-radius 8px
    margin .5rem
    display flex
    justify-content center
    align-items center
    color #1592ab
    font-weight bold
    font-size 18px

    path
        fill #1592ab

    button
        border none
        padding 1

.author
    font-family Chango
    font-size 24px
    text-align right
    width 100%
    color #1592ab
</style>
