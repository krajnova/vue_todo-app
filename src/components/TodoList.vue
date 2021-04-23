<template>
  <div>
    <h2 class="todo-list-header">Your todos</h2>

    <ul class="todo-list">
      <li v-for="(todo, id) in todos" :key="id" class="todo-list__item">
        <TodoItem :todo="todo" @delete-todo="$emit('delete-todo', id)" />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
  name: 'TodoList',
  components: {
    TodoItem,
  },

  props: ['todos'],
}
</script>

<style lang="scss" scoped>
.todo {
  &-list {
    display: inline-block;
    list-style: none;
    margin-top: 0;

    &,
    &-header {
      color: hsl(106, 63%, 60%);
    }

    &__item {
      cursor: pointer;
    }
  }
}
</style>
