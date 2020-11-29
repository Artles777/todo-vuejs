<template>
  <div class="todo">
    <h2 class="todo__title">Список задач</h2>

    <div class="navigation">
      <router-link class="navigation-link" to="/">&lt; Главная страница</router-link>
    </div>

    <AddTodo @add-todo="onSubmit" />

    <select v-model="filter">
      <option value="all">Все задачи</option>
      <option value="completed">Завершённые задачи</option>
      <option value="not-completed">Незавершённые задачи</option>
    </select>
    
    <hr />

    <Loading v-if="loading" />

    <Info :length="filteredTodos.length" v-if="loading === false" />
    <TodoList
      :todos="filteredTodos"
      @remove-todo="onRemove"
    />

    <Board
      v-if="filteredTodos
        .length === 0 && loading === false"
      @add-todo="onSubmit"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import Board from '@/components/Board'
import AddTodo from '@/components/AddTodo'
import Loading from '@/components/Loading'
import Info from '@/components/Info'

export default {
  name: 'App',
  data () {
    return {
      loading: false,
      todos: [],
      filter: 'all'
    }
  },
  computed: {
    filteredTodos () {
      if (this.filter === 'completed') {
        return this.todos.filter(todo => todo.completed)
      }

      else if (this.filter === 'not-completed') {
        return this.todos.filter(todo => !todo.completed)
      }

      else {
        return this.todos
      }
    }
  },
  components: {
    TodoList,
    Board,
    AddTodo,
    Loading,
    Info
  },
  methods: {
    onRemove (id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    onSubmit (todo) {
      this.todos.push(todo)
    }
  },
  created () {
    this.mounted
  },
  mounted () {
    this.loading = true
    fetch('https://jsonplaceholder.typicode.com/todos/?')
      .then(response => response.json())
      .then(todo => {
        this.todos = todo
        this.loading = false
      })
  }
}
</script>

<style lang="scss" scoped>
  .navigation {
    display: flex;
    position: absolute;
    margin-top: 0.3rem;

    &-link {
      font-weight: 700;
      color: #555 !important;
      text-decoration: none !important;

      &:hover {
        color: #00b84c !important;
      }
    }
  }
  select {
    margin-top: 1.2rem;
    margin-bottom: 1rem;
  }
</style>
