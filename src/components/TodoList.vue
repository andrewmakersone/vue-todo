<template>
  <div>

    <ul>
      <li v-for="(todo, index) in todos" :key="todo.name">
        <span>
          <label>
            <input type="checkbox" @change="todo.completed = !todo.completed">
          </label>
          <strong>{{index + 1}}.</strong>
          <span :class="{done: todo.completed}">{{todo.title | toUppercase}}</span>
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
    return {}
  },
  filters: {
    toUppercase (value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped lang="scss">
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
