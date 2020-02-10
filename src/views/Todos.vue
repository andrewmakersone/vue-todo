<template>
  <div>
    <h2>Your tasks:</h2>
    <AddTodo @add-todo="addTodo"></AddTodo>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <Loader v-if="loading"></Loader>
    <TodoList v-else-if="filteredTodos.length" :todos="filteredTodos" @remove-todo="removeTodo"></TodoList>
    <p v-else>Nothing here. Please, add todo!</p>
  </div>
</template>

<script>
import AddTodo from '../components/AddTodo'
import TodoList from '../components/TodoList'
import Loader from '../components/Loader'

export default {
  data () {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json
          this.loading = false
        }, 1000)
      })
  },
  computed: {
    filteredTodos () {
      if (this.filter === 'all') {
        return this.todos
      } else if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      } else if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      } else {
        return this.todos
      }
    }
  },
  methods: {
    addTodo (todo) {
      this.todos.push(todo)
    },
    removeTodo (id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  },
  components: {
    AddTodo, TodoList, Loader
  }
}
</script>

<style scoped lang="scss">
  select {
    display: block;
    margin: 20px 0 20px auto;
    text-align: right;
  }
</style>
