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

        <todo-list
          :todos="todos"
          @delete="deleteTodo"
          @done="done"
          class="mb-2"
        ></todo-list>

        <small>Total Todo: {{ totalTodo }}</small>
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
  mounted() {
    if (localStorage.getItem('todos') != null) {
     this.todos = JSON.parse(localStorage.getItem("todos")); 
    }
  },
  computed: {
    totalTodo() {
      return this.todos.length;
    },
  },
  methods: {
    add() {
      this.todos.unshift({
        activity: this.todo,
        isDone: false,
      });
      this.todo = "";
      this.saveToLocalStorage();
    },
    deleteTodo(todoIndex) {
      this.todos = this.todos.filter((todo, index) => index != todoIndex);

      this.saveToLocalStorage();
    },
    done(todoIndex) {
      console.log("done");
      this.todos = this.todos.filter((item, index) => {
        if (index == todoIndex) {
          item.isDone = !item.isDone;
        }

        return item;
      });

      this.saveToLocalStorage();
    },
    saveToLocalStorage() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
};
</script>
