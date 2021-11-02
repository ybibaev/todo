<script>
import TodoItems from "./TodoItems.vue";
import TodoInput from "./TodoInput.vue";

export default {
  components: { TodoItems, TodoInput },
  data() {
    const rawTodos = window.localStorage.getItem("todos");

    return {
      todos: (rawTodos && JSON.parse(rawTodos)) || [
        "Learn JavaScript",
        "Learn Vue",
        "Build something awesome",
      ],
    };
  },
  watch: {
    todos: {
      handler() {
        window.localStorage.setItem("todos", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
};
</script>

<template>
  <div class="todolist">
    <TodoInput :list="this.todos" placeholder="Just add a new task" />
    <TodoItems :list="this.todos" />
  </div>
</template>

<style scoped>
.todolist {
  margin: 60px;
  align-content: auto;
}
</style>
