<template>
  <div class="container">
    <h1>MY TO-DO LIST </h1>
    <form @submit.prevent="addTask">
      <input type="text" v-model="newTask" placeholder="Add task" />
      <button type="submit">Add</button>
    </form>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" :checked="task.done" @change="toggleDone(task)" />
        <span :class="{ done: task.done }">{{ task.text }}</span>
        <button @click="deleteTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, done: false });
        this.newTask = "";
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    toggleDone(task) {
      task.done = !task.done;
    },
  },
};
</script>

<style>
.container {
  text-align: center;
}

.done {
  text-decoration: line-through;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 10px;
  margin-top: 10px;
}

input[type="text"] {
  padding: 5px;
  border: none;
  border-radius: 5px;
  margin-right: 5px;
}

button {
  padding: 5px 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #3e8e41;
}

.done {
  text-decoration: line-through;
}
</style>
