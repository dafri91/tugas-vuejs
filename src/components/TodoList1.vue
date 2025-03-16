<script setup>
import { ref } from "vue";

const newTask = ref('')
const tasks = ref([])

const addTask = () => {
    const taskTrimmed = newTask.value.trim()

    if (taskTrimmed !== '' && !tasks.value.includes(taskTrimmed)) {
        tasks.value.push(taskTrimmed)
        newTask.value =''
    }
};

const removeTask = (index)=>{
    tasks.value.splice(index,1)
}

</script>

<template>
<div class="todo-container">
    <h2 class="title">To-Do List</h2>

    <div class="input-container">
        <input v-model="newTask" placeholder="tugas baru..." @keyup.enter = 'addTask'>
        <button @click="addTask"> Tambah</button>
    </div>

    <ul class="task-list">
        <li v-for="(task, index) in tasks" :key="index" class="task-item">
        <span class="task-text">{{ task }}</span>
        <button class="delete-btn" @click="removeTask(index)">Hapus</button>
        </li>
    </ul>

    <p v-if="tasks.length === 0" class="empty-message">Belum ada tugas!</p>
</div>
</template>

<style scoped>

.todo-container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 12px;
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  text-align: center;
}


.title {
  font-size: 24px;
  font-weight: bold;
  color: #222;
  margin-bottom: 16px;
}

.input-container {
  display: flex;
  gap: 10px;
  margin-bottom: 16px;
}

input {
  flex: 1;
  padding: 12px;
  border: 2px solid #ccc;
  border-radius: 8px;
  outline: none;
  font-size: 16px;
  transition: 0.3s;
}

input:focus {
  border-color: #007BFF;
  box-shadow: 0 0 6px rgba(0, 123, 255, 0.4);
}

button {
  padding: 12px 18px;
  background: #007BFF;
  border: none;
  border-radius: 8px;
  color: white;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
  box-shadow: 0 3px 6px rgba(0, 123, 255, 0.3);
}

button:hover {
  background: #0056b3;
}


.task-list {
  list-style: none;
  padding: 0;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f8f9fa;
  padding: 12px;
  border-radius: 8px;
  margin-bottom: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
  transition: 0.3s;
}

.task-item:hover {
  background: #e9ecef;
}


.task-text {
  color: #000;
  font-size: 16px;
  font-weight: 500;
}


.delete-btn {
  padding: 10px 24px;
  background: #FF4D4D;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
  min-width: 100px;
  text-align: center;
  box-shadow: 0 3px 6px rgba(255, 77, 77, 0.3);
}

.delete-btn:hover {
  background: #CC0000;
}

.empty-message {
  color: #888;
  font-size: 14px;
  margin-top: 10px;
}
</style>