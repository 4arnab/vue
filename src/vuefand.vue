<script setup>
import {ref, reactive} from 'vue'

// using reactive values in VUE 3 WITH COMPOSITION API
const user = reactive({
  name: "ahmed",
  age: 30,
  status: false,
  tasks: [1, 2, 3, 4, 5, 6]
})

const newTask = ref();

const changeStatus = () => user.status = !user.status

const addMoreTasks = ()=> {
  if(newTask.value.trim() !==''){
    user.tasks.push(newTask.value)
    newTask.value = "";
  }else{
    alert("please type a text to add new task")
  }
}

const deleteTask = (index)=>{
  console.log(index)
  user.tasks.splice(index, 1);// = user.tasks.filter(item => item !== task)
}

</script>

<template>
  <h1 v-if="user.status">hello, from vue</h1>
  <h1 v-else>user is not active</h1>
  <ul v-if="user.tasks.length">
    <li v-for="(task, index) in user.tasks" :key="task">
       <span>{{ task }}</span> <button @click="deleteTask(index)">delete </button>
    
    </li>
  </ul>
  <p v-else> No more tasks</p>

<form @submit.prevent="addMoreTasks">
  <label for="tastName">Task Name</label>
  <input type="text" placeholder="Add new task" name="taskName" v-model="newTask">

  <button type="submit">submit</button>
</form>
  <button @click="changeStatus">change status</button>
  <button @click="addMoreTasks">add more tasks</button>
</template>

<style scoped></style>
