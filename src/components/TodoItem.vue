<template>
  <p @click="markComplete" class="todo-container">
    <span :class="{ completed: todo.completed }">{{ todo.title }}</span>
    <button class="remove-btn" @click="$emit('delete-todo', todo.id)">
      &times;
    </button>
  </p>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],

  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed
    },
  },
}
</script>

<style lang="scss" scoped>
$font-size: 1.4rem;

.todo-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: $font-size;

  .remove-btn {
    background: none;
    border: none;
    color: #f00;
    font-weight: bold;
    cursor: pointer;
    font-size: $font-size;
  }
}

.completed {
  text-decoration: line-through;
}
</style>
