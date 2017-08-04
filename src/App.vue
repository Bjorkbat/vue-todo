<template>

  <div id="app">

    <form v-on:submit.prevent="addToDo">
      <input type="text"
        placeholder="Type your new to-do here"
        v-model="todo">
    </form>

  </div>

</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      todo: '',
      todos: [],
      msg: 'Welcome to Your Vue.js App'
    }
  },

  methods: {
    addToDo: function() {

      // Push the todo typed inside the input into an array called todos
      this.todos.push(this.todo);
      this.todo = '';

    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
