<template>
  <main>

    <h1> Task Board </h1>
    <p> Create a list of tasks </p>

    <div class="create-new"> 
      <input 
      type="text" 
      v-model="newTask" 
      placeholder="Add a new task" 
      @keypress.enter="addTask"
      />
      <button @click.prevent="addTask"> Add </button>
    </div>

    <div class="tasks">
      <Task 
       v-for="(task, index) in $store.state.tasks" 
       :key="index"
       :task="task"
       />
    </div>

  </main>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      newTask: ""
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit("ADD_TASK", this.newTask)
        this.newTask = ""
      }
    }
  }
}
</script>
