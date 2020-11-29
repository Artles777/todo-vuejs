<template>
  <div>
    <p class="todo-info">
      Количество задач: {{ length }}
    </p>
  </div>
</template>

<script>
export default {
  props: ['length']
}
</script>

<style scoped>
  div {
    text-align: left;
  }
  p {
    font-weight: 700;
    font-size: 1.1rem;
  }
</style>
