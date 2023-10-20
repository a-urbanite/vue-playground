<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @btn-click="$emit('toggle-add-task')"
      :btnText="showAddTask ? 'Close' : 'Add Task'"
      :btnColor="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>

<script>
import Button from "./Button.vue";

export default {
  name: "MainHeader",
  props: {
    title: {
      type: String,
      default: "title missing",
    },
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  emits: ["toggle-add-task"],
};
</script>
