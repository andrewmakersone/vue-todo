<template>
  <div id="app">
<!--    <div id="nav">-->
<!--      <router-link to="/">Home</router-link> |-->
<!--      <router-link to="/about">About</router-link>-->
<!--    </div>-->
<!--    <router-view/>-->
    <h1>Todo application</h1>
    <AddTodo @add-todo="addTodo"></AddTodo>
    <hr>
    <TodoList :todos="todos" @remove-todo="removeTodo"></TodoList>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo'
import TodoList from './components/TodoList'
export default {
  name: 'app',
  data () {
    return {
      todos: [
        { id: 1, name: 'Сходить в магазин', completed: false },
        { id: 2, name: 'Приготовить обед', completed: false },
        { id: 3, name: 'Написать приложение на Vue', completed: false }
      ]
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
    AddTodo, TodoList
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
