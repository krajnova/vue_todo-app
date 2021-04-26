<template>
  <div id="app">
    <TodoList :todos="sortedTodos" @delete-todo="deleteTodo" />
    <AddTodo @add-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import AddTodo from './components/AddTodo'

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
          title: 'Go workout',
          completed: false,
        },
        {
          title: 'Do laundry',
          completed: false,
        },
        {
          title: 'Cook food',
          completed: false,
        },
        {
          title: 'Clean up room',
          completed: false,
        },
        {
          title: 'Finish work',
          completed: false,
        },
      ],
    }
  },
  created() {
    let todos = window.localStorage.getItem('todos')
    if (todos) {
      this.todos = JSON.parse(todos)
    }
  },
  watch: {
    todos: {
      immediate: false,
      handler(newVal) {
        window.localStorage.setItem('todos', JSON.stringify(newVal))
      },
    },
  },
  computed: {
    sortedTodos() {
      return [...this.todos].sort(({ completed }) => (completed ? 1 : -1))
    },
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo)
    },
    deleteTodo(id) {
      this.todos.splice(id, 1)
    },
  },
}
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
  background-color: hsl(65, 100%, 93%);

  display: flex;
  justify-content: center;
}
</style>
