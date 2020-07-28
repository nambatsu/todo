<template>
  <div>
    <div>TaskList</div>
    <div v-for="task in tasks" :key="task.name">
      <div class="name">タスク: {{ task.name }}</div>
      <div v-if="task.status">☑</div>
      <div v-if="!task.status">
        ☐
        <button @click="statusChange(task)">完了</button>
      </div>
    </div>
    <div>
      <label>
        タスク
        <input type="text" v-model="newTaskName" />
      </label>
      <button @click="addTask">add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  data() {
    return {
      tasks: [
        { name: "課題", status: true },
        { name: "掃除", status: false }
      ],
      newTaskName: ""
    };
  },
  methods: {
    addTask() {
      if (this.newTaskName != "") {
        this.tasks.push({ name: this.newTaskName, status: false });
        this.newTaskName = "";
      }
    },
    statusChange(item) {
      item.status = true;
    }
  }
};
</script>

<style></style>
