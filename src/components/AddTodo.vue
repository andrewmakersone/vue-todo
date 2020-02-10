<template>
  <form class="add-todo" @submit.prevent="onSubmit(title)">
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
          id: (Math.random() * 10000 + 200).toFixed(0),
          title: title,
          completed: false
        }
        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .add-todo {
    display: block;
    font-size: 14px;
    margin: 20px auto;
    input {
      width: 50%;
    }
    input, button {
      padding: 5px;
    }
    button {
      margin-left: -1px;
    }
  }
</style>
