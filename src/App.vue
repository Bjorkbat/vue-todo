<template>

  <div id="app">

    <form v-on:submit.prevent="addToDo">
      <input type="text"
        placeholder="Type your new to-do here"
        v-model="todo">
    </form>

    <ul>
      <!-- thing on the right side of the "in" is the array
           thing on the left side of the "in" is the item in the array -->
      <todo-item
        v-for="todo in todos"
        v-bind:todo="todo"
        v-on:delete="deleteToDo">
      </todo-item>
    </ul>

  </div>

</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
  name: 'app',
  components: { TodoItem },
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

    },

    deleteToDo: function(todo) {

      for(var i = 0; i < this.todos.length; i ++) {
        if (this.todos[i] == todo) {
          // Delete this todo (and just this one) from the array
          this.todos.splice(i, 1);
        }
      }

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

a {
  color: #42b983;
}
</style>
