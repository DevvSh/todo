<template>
  <div>
    <h1 class="app-title">Todo List</h1>
    <input type="text" class="todo-input" placeholder="What needs to be done" v-model="newtask" @keyup.enter="addTask">
    <div v-for="task in tasks" :key="task.id" class="task-item">
      <div class="task-text">
        {{ task.title }}
      </div>
      <div class="remove-item" @click="removeTask(task.id)">
        &times;
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data() {
    return {
      newtask: '',
      idForTask: '3',
      tasks: [
        {
          id: '1',
          title: "Shopping",
          completed: false,
        },
        {
          id: '2',
          title: "Kill people",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTask() {
      if (this.newtask.trim().length === 0) {
        return;
      }
      this.tasks.push({
        id: this.idForTask,
        title: this.newtask,
        completed: false,
      });

      this.newtask = '';
      this.idForTask++;
    },
    removeTask(taskId) {
      this.tasks = this.tasks.filter((task) => task.id !== taskId);
    },
  },
};
</script>

<style>
.app-title {
  text-align: center;
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.todo-input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
}

.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #f8f8f8;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.task-text {
  flex: 1;
  font-size: 18px;
  color: #333;
}

.remove-item {
  font-size: 20px;
  cursor: pointer;
  color: #ff6347;
}
</style>
