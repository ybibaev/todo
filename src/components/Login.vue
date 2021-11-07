
<script>
export default {
    props: ["isLogged"],
    computed: {
        title() {
            return this.isLogged ? "You are logged" : "Anonymous"
        }
    }
}
</script>


<template>
  <button :title="title" class="btn btn-primary" @click="isLogged = !isLogged">
    <i v-if="isLogged" class="icon icon-shutdown"></i>
    <i v-else class="icon icon-people"></i>
  </button>
</template>