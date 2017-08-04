<template>
  <li id="TodoItem">
    {{ todo }}
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo']
}
</script>
