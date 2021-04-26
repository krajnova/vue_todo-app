<template>
  <p class="todo-container">
    <input
      v-if="editing"
      v-model="todo.title"
      type="text"
      :class="{ completed: todo.completed }"
    />
    <span v-else @click="markComplete" :class="{ completed: todo.completed }">
      {{ todo.title }}
    </span>

    <span class="todo-controls">
      <button class="edit-btn" @click="editTodo">
        {{ editing ? 'Save' : 'Edit' }}
      </button>

      <button class="remove-btn" @click="$emit('delete-todo', todo.id)">
        &times;
      </button>
    </span>
  </p>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],

  data() {
    return {
      editing: false,
    }
  },

  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed
    },
    editTodo() {
      this.editing = !this.editing
    },
  },
}
</script>

<style lang="scss" scoped>
$font-size: 1.4rem;

.todo {
  &-container {
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

  &-controls {
    margin-left: 1rem;
  }
}

.completed {
  text-decoration: line-through;
}
</style>
