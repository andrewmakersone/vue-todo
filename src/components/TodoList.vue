<template>
  <div>
    <ul>
      <li v-for="(todo, i) in todos" v-bind:index="i" :key="todo.name">
        <span>
          <label>
            <input type="checkbox" @change="todo.completed = !todo.completed">
          </label>
          <strong>{{todo.id}}.</strong>
          <span :class="{done: todo.completed}">{{todo.name}}</span>
        </span>
        <button class="remove-button" @click="$emit('remove-todo', todo.id)">&times;</button>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  components: {},
  props: ['todos'],
  data () {
    return {
      newTask: ''
    }
  }
}
</script>

<style scoped lang="scss">
  .add-task-input {
    display: block;
    font-size: 14px;
    margin: 25px auto;
    input, button {
      padding: 5px;
    }
    button {
      margin-left: -1px;
    }
  }
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    li {
      border: 1px solid lightgrey;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.5rem 1rem;
      margin-bottom: 1rem;
      span {
        input {
          margin-right: 0.5rem;
        }
        strong {
          margin-right: 0.5rem;
        }
      }
      button.remove-button {
        cursor: pointer;
        border: none;
        border-radius: 50%;
        color: white;
        background-color: orangered;
        width: 20px;
        height: 20px;
        max-width: 20px;
        max-height: 20px;
      }
    }
    .done {
      text-decoration: line-through;
    }
  }
</style>
