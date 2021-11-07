<script>
import Login from "./Login.vue"


export default {
  data() {
    return {
      rawInput: "",
    };
  },
  components: { Login },
  props: ["list", "placeholder"],
  methods: {
    addItem(event) {
      if (this.rawInput === "") {
        return;
      }

      this.list.push(this.rawInput);
      this.rawInput = "";

      if (event.type === "keyup") {
        event.target.value = "";
      }
    },
  },
};
</script>


<template>
  <div class="input-group">
    <Login />
    <input
      v-model.trim.lazy="rawInput"
      class="form-input"
      @keyup.enter="addItem"
      :placeholder="placeholder"
    />
    <button @click="addInput" class="btn btn-primary">Add</button>
  </div>
</template>