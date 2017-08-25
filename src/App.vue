<template>

  <div id="app">

    <form v-on:submit.prevent="addToDo">
      <!-- Keeping it simple with the form.  It has a single input element.
        Notice that it has a "v-model" directive to bind it to the "todo"
        attribute returned by the data function -->
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

// You can import other vue components like so.
import TodoItem from './TodoItem.vue';

export default {
  name: 'app',

  // Vue components can import other components.  That's what we're doing here
  // with TodoItem
  components: { TodoItem },

  // Data contains the internal bits and pieces of data used by our component.
  // It's a little odd, but data is a function, not an object, but we treat it
  // a lot like an object.
  data () {

    // All our data function does is return an object with some fairly simple
    // attributes attached to it.
    return {
      todo: '',
      todos: [],
      msg: 'Welcome to Your Vue.js App'
    }

  },

  methods: {

    // Adds new todos to our list.  Pretty simple really.  Just adds the
    // todo from the form to an array and clears the form input
    addToDo: function() {

      // Push the todo typed inside the input into an array called todos
      this.todos.push(this.todo);
      this.todo = '';

    },

    // Removes todos from our list.  Triggered by a click event
    deleteToDo: function(todo) {

      for(var i = 0; i < this.todos.length; i ++) {
        if (this.todos[i] == todo) {
          // Delete this todo (and just this one) from the array using the
          // splice method
          // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
          this.todos.splice(i, 1);
        }
      }

    }

  }
}
</script>

<style lang="scss">
/**
 * Remember, you can add css (or in this case, scss) directly inside a
 * component.  It's often a good idea to do so too, since most of the time a
 * particular snippet of CSS only affects a particular Vue component
 */
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
