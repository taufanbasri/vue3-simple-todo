<template>
  <div class="container mt-4">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">SIMPLE TODO APP</h5>
        <div class="row">
          <div class="col-10">
            <input v-model="todo" type="text" class="form-control" />
          </div>
          <div class="col-2">
            <button @click="add" class="btn btn-success">Add</button>
          </div>
        </div>

        <div>
          <ul class="list-group mt-4">
            <li v-for="todo in todos" :key="todo" class="list-group-item">{{ todo }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: "",
      todos: [],
    };
  },
  methods: {
    add() {
      this.todos.push(this.todo);
    },
  },
};
</script>
