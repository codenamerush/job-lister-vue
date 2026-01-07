<script>
  export default {
    name: 'App',
    data() {
      return {
        name: 'John Doe',
        status: 'inactive',
        tasks: ['Task 1', 'Task 2', 'Task 3'],
      }
    }
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
</template>

