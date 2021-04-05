<template>
  <div id="tasks">
    <button
      class="btn round-icon"
      v-on:click="addTask('My new task', 'My new description'), resetForm()"
      @click="addTask(newTitle, newDescription)">+</button>

    <div class="task-card new-task">
      <div>
        <input
          type="text"
          placeholder="What would you like to do?"
          v-model="newTitle"
        />
        <textarea
      placeholder="Add some details about your task..."
      v-model="newDescription"
        ></textarea>
      </div>
    </div>
    <div v-if="tasks.length > 0">
      <TaskCard
        v-for="(task, index) in tasks"
        :key="index"
        :title="task.title"
        :description="task.description"
        :done="task.done">
      </TaskCard>
    </div>
    <p v-else>You don't have any tasks yet 😢</p>
  </div>
</template>
<script>
import TaskCard from './TaskCard'
export default {
  components: { TaskCard },
  data() {
    return {
      tasks: [],

    };
  },
  methods: {
    addTask(title, description, done = false) {
      this.tasks.unshift({ title, description, done});
    },
    resetForm() {
      this.newTitle= "";
      this.newDescription = "";
    }
  },
}
</script>
