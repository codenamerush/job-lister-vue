<script setup>
  import { ref, onMounted } from 'vue';
  
  const name = ref('John Doe');
  const status = ref('inactive');
  const tasks = ref(['Task 1', 'Task 2', 'Task 3']);
  const newTask = ref('');

  const changeStatus = () => {
    status.value = status.value === 'active' ? 'inactive' : 'active';
  }
  
  const addTask = () => {
    if (newTask.value.trim() === '') return;
    tasks.value.push(newTask.value.trim());
    newTask.value = '';
  }

  const removeTask = (index) => {
    tasks.value.splice(index, 1);
  }

  onMounted(async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/todos');
      const data = await response.json();
      tasks.value = data.map(todo => todo.title);
    } catch (error) {
      console.error('Error fetching tasks:', error);
    }
  })
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'inactive'">User is Inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <br/>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Add</button>
  </form>
  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="removeTask(index)">x</button>
    </li>
  </ul>
  <br/><br/>
  <button @click="changeStatus"> Change Status </button>
</template>

