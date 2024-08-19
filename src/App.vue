<script setup>
import {ref, reactive} from 'vue'

// using reactive values in VUE 3 WITH COMPOSITION API
const user = reactive({
  name: "ahmed",
  age: 30,
  status: false,
  tasks: [1, 2, 3, 4, 5, 6]
})

const changeStatus = () => user.status = !user.status
const addMoreTasks = ()=> user.tasks.push(user.tasks.length + 1)

</script>

<template>
  <h1 v-if="user.status">hello, from vue</h1>
  <h1 v-else>user is not active</h1>
  <ul>
    <li v-for="task in user.tasks" :key="task">{{ task }}</li>
  </ul>

  <button @click="changeStatus">change status</button>
  <button @click="addMoreTasks">add more tasks</button>
</template>

<style scoped></style>
