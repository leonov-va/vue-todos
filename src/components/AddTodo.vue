<template>
  <form @submit.prevent="onSubmit">
    <input type="text" placeholder="Enter text" v-model="title" />
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };

        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input {
  width: 100%;
  height: 40px;
  padding: 0 20px;
}
button {
  flex-shrink: 0;
  width: 100px;
  margin-left: 20px;
  cursor: pointer;
}
</style>
