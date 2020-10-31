<template>
  <div :class="{ 'completed': todo.completed }">
    <p @click="markComplete">
      {{ todo.title }}
      <button
        class="remove-btn"
        @click="$emit('delete-todo', todo.id)"
      >
        X
      </button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: [
    "todo"
  ],

  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}

.remove-btn {
  background: none;
  border: none;
  color: #f00;
  border-radius: 50%;
  font-weight: bold;
  cursor: pointer;
}

</style>
