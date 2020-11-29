<template>
  <div>
    <ul class="todo__list">
      <TodoItem
        v-for="(todo, id) of todos"
        :key="todo.id"
        :todo="todo"
        :id="id"
        @remove-todo="onRemove"
        />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    onRemove (id) {
      this.$emit('remove-todo', id)
    }
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>
