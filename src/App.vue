<template>
  <div id="app">
    <h1>Simple Todos</h1>
    <Todos @closeTodo="_closeTodo" />

    <h1 :class="classObject">Bind class object</h1>
    <h2 :style="{ color: active ? 'red' : 'green', fontSize: '14px'}">inline css</h2>

    <ComputedWatch :firstNameProps="name" />
    <button type="button" @click="changeName">change firstname</button>

    <div v-if="Math.random() > 0.5">
      Tài
    </div>
    <div v-else-if="Math.random() < 1.5">
      xiu
    </div>
    <div v-else>
      xiu small
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import ComputedWatch from "./components/ComputedWatch";

export default {
  components: {
    Todos,
    ComputedWatch
  },
  data() {
    return {
      name: 'niem',
      active: true,
    }
  },
  methods: {
    onChangeCheckBox(event) {
      this.accept = event.target.checked
      console.log('onChangeCheckBox', event.target.checked)
    },
    changeName() {
      this.name = 'test'
    },
    _closeTodo(id) {
      console.log('_closeTodo: ', id)
    }
  },
  computed: {
    classObject() {
      return {
        active: this.active,
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 768px;
  margin: 60px auto;
}
h1 {
  padding: 0 0 20px 0;
  margin: 0;
}
</style>
