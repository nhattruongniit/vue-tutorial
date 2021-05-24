<template>
  <div>
    <input type="text" v-model="newTasks" />
    <button type="button" @click="addNewTask">Add Task</button>
    <br /><br />
    <div v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{underline: todo.done}">{{ todo.text }}</span>
      <button type="button" @click="closeTodo(todo.id)">X</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTasks: '',
      todos: [
        { id: 1, text: 'learn vue', done: false },
        { id: 2, text: 'learn javascript', done: false },
        { id: 3, text: 'learn react', done: false },
      ]
    }
  },
  methods: {
    addNewTask() {
      this.todos.push({
        id: Date.now(),
        text: this.newTasks,
        done: false
      })
    },
    closeTodo(id) {
      this.$emit('closeTodo', id)
    }
  }
};
</script>

<style>
.underline {
  text-decoration: line-through;
}
</style>
