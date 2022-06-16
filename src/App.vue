<template>
  <div class="container mt-4">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">SIMPLE TODO APP</h5>
        <div class="row">
          <div class="col-10">
            <input
              v-model="todo"
              @keyup.enter="add"
              type="text"
              class="form-control"
            />
          </div>
          <div class="col-2">
            <button @click="add" class="btn btn-success">Add</button>
          </div>
        </div>

        <todo-list :todos="todos" @delete="deleteTodo"></todo-list>
      </div>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoList,
  },
  data() {
    return {
      todo: "",
      todos: [],
    };
  },
  methods: {
    add() {
      this.todos.unshift(this.todo);
      this.todo = "";
    },
    deleteTodo(todoIndex) {
      this.todos = this.todos.filter((todo, index) => index != todoIndex);
    },
  },
};
</script>
