<template>
  <form class="todo-add" @submit.prevent="onSubmit">
    <span class="todo-add-wrapper">
      <input class="todo-add-field" type="text" v-model="title" @keydown.delete="title = null">
      <button class="todo-add-rm" @mousedown.exact="title = null" v-if="title">&times;</button>
    </span>
    <button class="todo-add-adding" type="submit">Добавить</button>
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
    onSubmit () {
      if (this.title.trim()) {
        const NewTodo = {
          id: Math.floor(Math.random() * Math.floor(1000000)),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', NewTodo)
      }
      this.title = null
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  span {
    position: relative;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 5px 35px 5px 10px;
    margin-right: 10px;
  }
  input {
    width: 40vw;
    margin: 10px;
    outline: none;
    border: none;
    margin: 0;
    background: inherit;
  }
  button {
    padding: 5px 15px;
  }
  .todo-add-rm {
    position: absolute;
    border: none;
    outline: none;
    background: none;
    font-size: 1rem;
    padding: 0;
    margin: 0 10px;
    cursor: pointer;
  }
</style>
