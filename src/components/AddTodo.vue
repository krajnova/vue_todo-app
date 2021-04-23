<template>
  <div>
    <input class="add-todo-input" type="text" v-model="title" name="title" />
    <button @click="addTodo()" class="add-todo-btn">Add</button>
  </div>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
    }
  },

  methods: {
    addTodo() {
      if (this.title === '') {
        return
      }

      const newTodo = {
        title: this.title,
        completed: false,
      }

      this.$emit('add-todo', newTodo)
      this.title = ''
    },
  },
}
</script>

<style scoped>
.add-todo-btn {
  background-color: hsl(106, 63%, 81%);
  color: #fff;
  border: 1px solid hsl(106, 63%, 81%);
  padding: 7px;
  border-radius: 0 10px 10px 0;
  cursor: pointer;
}

.add-todo-btn:hover,
.add-todo-btn:focus {
  background-color: hsl(106, 63%, 50%);
}

.add-todo-input {
  border: 1px solid hsl(106, 63%, 81%);
  padding: 7px;
  border-radius: 10px 0 0 10px;
}

.add-todo-input:focus {
  border-color: hsl(106, 63%, 50%);
}

.add-todo-input:focus,
.add-todo-btn:focus {
  outline: none;
}
</style>
