<template>
  <form class="add-task-input" @submit.prevent="onSubmit(title)">
    <span>Add new task: </span>
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit (title) {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          name: title,
          completed: false
        }
        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
  button {
    margin-left: -1px;
  }
</style>
