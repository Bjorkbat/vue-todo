<template>
  <li>

    {{ todo }}

    <a href="#">Edit</a>
    <a href="#" v-on:click.prevent="deleteToDo">Delete</a>

  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo'],

  methods: {

    deleteToDo: function() {
      this.$emit('delete', this.todo);
    }

  }
}
</script>
