<script>
import TodoItem from "./TodoItem.vue";

export default {
  components: { TodoItem },
  props: ["list"],
  methods: {
    removeItem(position, target) {
      target.classList.add("done");

      setTimeout(() => {
        this.list.splice(position, 1);
        target.classList.remove("done");
      }, 300);
    },
  },
};
</script>

<template>
  <ol>
    <TodoItem
      v-for="(todo, index) in list"
      :key="index"
      :title="todo"
      :position="index"
      @remove="removeItem"
    />
  </ol>
</template>