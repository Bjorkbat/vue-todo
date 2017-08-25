<template>
  <li>
    <!-- This component is simply a list item element with some link tags
      thrown in.  Still, it's better "componentize" this stuff rather than
      repeat yourself -->

    <!-- Here we're using "mustaches" to render the value of todo as text inside
      our html. -->
    {{ todo }}

    <!-- we can attach v-on.click to our elements to register a function when
      a click event is triggered -->
    <a href="#" v-on:click.prevent="editToDo">Edit</a>
    <a href="#" v-on:click.prevent="deleteToDo">Delete</a>

  </li>
</template>

<script>
export default {
  name: "TodoItem",

  // Here we can define what sort of props a vue component can accept
  // from parent components.  In this case, our TodoItem just accepts a todo
  // prop (which we can pass into this component using v-bind:todo)
  props: ['todo'],

  methods: {

    // We're not going to delete the todo here.  Instead, we're just going to
    // trigger a special event, namely a delete event.
    deleteToDo: function() {
      this.$emit('delete', this.todo);
    },

    // Just like with deleteTodo, we're going to emit an edit event when this
    // function is called, and let the parent handle the business of editing
    // the todo
    editToDo: function() {
      this.$emit('edit', this.todo);
    }

  }
}
</script>
