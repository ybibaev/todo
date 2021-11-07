<script>
import TodoItems from "./TodoItems.vue";
import TodoInput from "./TodoInput.vue";

export default {
  components: { TodoItems, TodoInput },
  data() {
    const rawTodos = window.localStorage.getItem("todos");

    return {
      isLogged: false,
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
  <div class="todolist column col-8">
    <TodoInput :list="this.todos" placeholder="Just add a new task" />
    <TodoItems :list="this.todos" />
  </div>
</template>

<style>
.todolist {
  margin: 5% auto;
  max-width: 600px;
  overflow-wrap: break-word;
}
</style>
