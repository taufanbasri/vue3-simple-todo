<template>
  <div>
    <ul class="list-group mt-4">
      <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
        <div class="row">
          <div class="col">
            <span v-if="todo.isDone">
              <del>{{ todo.activity }}</del>
            </span>
            <span v-else>{{ todo.activity }}</span>
          </div>
          <div class="col-auto">
            <div class="row gx-2">
              <div class="col">
                <button @click="done(index)" class="btn btn-primary">
                  Done
                </button>
              </div>
              <div class="col">
                <button @click="del(index)" class="btn btn-danger">X</button>
              </div>
            </div>
          </div>
        </div>
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
  methods: {
    del(index) {
      this.$emit("delete", index);
    },
    done(index) {
      this.$emit("done", index);
    },
  },
};
</script>
