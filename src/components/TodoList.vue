<template>
  <div>
    <h2 class="todo-list-header">Your todos</h2>

    <ul class="todo-list">
      <li :key="todo.id" v-for="todo in todos" class="todo-list__item">
        <TodoItem
          :todo="todo"
          @delete-todo="$emit('delete-todo', todo.id)"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
  name: 'TodoList',
  components: {
    TodoItem
  },

  props: [
    "todos"
  ]
}
</script>

<style scoped>
.todo-list-header,
.todo-list {
  color: hsl(106, 63%, 60%);
}

</style>
