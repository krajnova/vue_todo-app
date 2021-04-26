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

<style lang="scss" scoped>
$btn-background: hsl(106, 63%, 81%);
$transition: all 0.2s ease-in-out;

.add-todo {
  &-btn {
    background-color: $btn-background;
    color: #fff;
    border: 1px solid hsl(106, 63%, 81%);
    padding: 7px;
    border-radius: 0 10px 10px 0;
    cursor: pointer;
    transition: $transition;
    outline: 0;

    &:hover,
    &:focus {
      background-color: darken($btn-background, 20%);
    }
  }

  &-input {
    border: 1px solid hsl(106, 63%, 81%);
    padding: 7px;
    border-radius: 10px 0 0 10px;
    outline: 0;
    transition: $transition;

    &:focus {
      border-color: hsl(106, 63%, 50%);
    }
  }
}
</style>
