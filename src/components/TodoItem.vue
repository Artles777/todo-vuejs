<template>
  <li class="todo__item">
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" :checked="todo.completed" v-on:change="todo.completed = !todo.completed" />
      <strong>
        {{ id + 1 }}
      </strong>
      {{ todo.title | upperCase }}
    </span>

    <button class="rm" @click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    id: Number
  },
  filters: {
    upperCase (value) {
      return value[0].toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #cccccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }
  span {
    display: flex;
    align-items: center;
  }
  strong {
    margin-right: .3rem;
  }
  input {
    margin: 0;
    margin-right: 1rem;
    width: 1rem;
    height: 1rem;
  }
  button {
    border: 1px solid #cccccc;
    background: none;
    font-size: .8rem;
    border-radius: 4px;
    outline: none;
  }
  button:hover {
    border: 1px solid #aaaaaa;
    background: #eeeeee;
    cursor: pointer;
  }
  .done {
    text-decoration: line-through;
  }
</style>
