<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <todo-list v-bind:todos="todos" />
    <create-todo v-on:create-todo="addTodo" />
  </div>
</template>

<script>

// import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  methods: {
    addTodo( todo ) {
      this.todos.push( todo );
    },
  },
  // data function provides data to the template
  data() {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        tags: ['t1', 't2'],
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        tags: ['t2', 't3'],
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        tags: ['t3', 't4'],
        done: false,
      }, {
        title: 'Todo D',
        project: 'Project D',
        tags: [],
        done: false,
      }],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
