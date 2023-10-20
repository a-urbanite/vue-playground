<template>
  <div class="container">
    <Header
      title="Task Tracker"
      @toggle-add-task="onToggleAddTask"
      :showAddTask="showAddTask"
    />
    <AddTask
      v-show="showAddTask"
      @toggle-add-task="onToggleAddTask"
      @add-new-task="onAddNewTask"
    />
    <TodoTasks
      @toggle-reminder="onToggleReminder"
      @delete-task="onDeleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import TodoTasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: { Header, TodoTasks, AddTask },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Dr Appointment",
        day: "march 1st",
        reminder: true,
      },
      {
        id: 2,
        text: "feed the cat",
        day: "march 5th",
        reminder: true,
      },
      {
        id: 3,
        text: "clean house",
        day: "march 16th",
        reminder: true,
      },
      {
        id: 4,
        text: "pick up pictures",
        day: "april 2nd",
        reminder: false,
      },
    ];
  },
  methods: {
    onToggleReminder(id) {
      const newTasks = this.tasks.map((task) => {
        return task.id === id ? { ...task, reminder: !task.reminder } : task;
      });
      this.tasks = newTasks;
    },
    onDeleteTask(id) {
      if (confirm("are you sure?")) {
        this.tasks = this.tasks.filter((task) => {
          return task.id !== id;
        });
      }
    },
    onAddNewTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    onToggleAddTask() {
      console.log("sadasds");
      this.showAddTask = !this.showAddTask;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Poppins", sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
