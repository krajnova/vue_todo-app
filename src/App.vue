<template>
  <div id="app">
    <TodoList :todos="todos" @delete-todo="deleteTodo" />
    <AddTodo @add-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
  components: {
    TodoList,
    AddTodo,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Go workout',
          completed: false
        },
        {
          id: 2,
          title: 'Do laundry',
          completed: false
        },
        {
          id: 3,
          title: 'Cook food',
          completed: false
        },
        {
          id: 4,
          title: 'Clean up room',
          completed: false
        },
        {
          i: 5,
          title: 'Finish work',
          completed: false
        },
      ]
    }
  },
  methods: {
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    }
  }
}
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
  background-color: hsl(65, 100%, 93%);
}
</style>
