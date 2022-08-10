<template>
  <div :class="`task ${task.done ? 'is-complete' : ''}`">
    <div class="content">
      {{ task.content }}
    </div>    
    <div class="buttons">
      <button @click.prevent='changeTask'> {{ task.done ? 'Undo': 'Done' }} </button>
      <button class="delete" @click.prevent="deleteTask"> Delete </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: ['task'],
  methods: {
    changeTask () {
      this.$store.commit('TOGGLE_TASK', this.task)
    },
    deleteTask () {
      this.$store.commit('REMOVE_TASK', this.task)
    }
  },
}
</script>