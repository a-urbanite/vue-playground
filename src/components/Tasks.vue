<template>
  <div v-for="task in tasks" :key="task.id">
    <Task
      @delete-task="(id) => $emit('delete-task', id)"
      @toggle-reminder="(id) => $emit('toggle-reminder', id)"
      :task="task"
    />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "TodoTasks",
  props: {
    tasks: Array,
  },
  components: { Task },
  emits: ["delete-task", "toggle-reminder"],
};
</script>
