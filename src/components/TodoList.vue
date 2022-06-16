<template>
  <div>
    <ul class="list-group mt-4">
      <li v-for="todo in todos" :key="todo" class="list-group-item">
        {{ todo }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      default: [],
    },
  },
};
</script>
