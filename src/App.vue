<script setup>
  import { ref } from 'vue';
  
  const name = ref('John Doe');
  const status = ref('inactive');
  const tasks = ref(['Task 1', 'Task 2', 'Task 3']);
  const changeStatus = () => {
    status.value = status.value === 'active' ? 'inactive' : 'active';
  }
  
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'inactive'">User is Inactive</p>

  <h3>Tasks</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <br/><br/>
  <button @click="changeStatus"> Change Status </button>
</template>

