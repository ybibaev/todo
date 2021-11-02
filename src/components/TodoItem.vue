<script>
export default {
  props: ["title", "position"],
  emits: ["remove"],
};
</script>

<template>
  <li @click="$emit('remove', position, $event.target)">
    {{ title }}
  </li>
</template>

<style scoped>
li {
  cursor: pointer;
}

.done {
  text-decoration: line-through;
}
</style>
