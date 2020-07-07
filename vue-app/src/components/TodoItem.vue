<template>
  <div>
    <div class="todo-item" v-for="todo in allTodos" :key="todo.id">
      <p>
        <input type="checkbox" name="" id="" v-on:change="markComplete" />
        {{ todo.title }}
        <button v-on:click="$emit('del-todo', todo.id)" class="del">x</button>
      </p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "TodoItem",
  computed: mapGetters(["allTodos"]),
  methods: {
    ...mapActions(["fetchTodos"]),
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
  created() {
    this.fetchTodos();
  },
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
