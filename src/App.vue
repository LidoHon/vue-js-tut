<script setup>
import { ref, onMounted } from 'vue';

    const name =ref('lido');
    const status=ref('active');
    const tasks=ref(['task1','task2', 'task3', 'task4']);
    const newTask = ref('')
    // const link='https://google.com';
    const toggleStatus=()=>{
      if(status.value==='active'){
        status.value='pending';
      }else if(status.value==='pending'){
        status.value='inactive';
      }else{
        status.value='active';
      }
    }
    const addTask=()=>{
      if(newTask.value.trim()!==''){
        tasks.value.push(newTask.value);
        newTask.value='';
      }
      
    }
    const deleteTask=(index)=>{
      tasks.value.splice(index,1);
    }
   onMounted(async ()=>{
    try {
      const res = await fetch('https://jsonplaceholder.typicode.com/todos');
      const data = await res.json();
      tasks.value = data.map((task)=>task.title);
    } catch (error) {
      console.log(error);
    }
     
   })

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status==='active'">user is active</p>
  <p v-else-if="status==='pending'">user is pending</p>
  <p v-else=>user is not active</p>

  <form @submit.prevent="addTask">
    <label for="newTask">add task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask"/>
    <button type="submit">add</button>
  </form>


  <h3>tasks</h3>
  <ul>
    <li  v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>

    </li>
  </ul>
  <!-- <a v-bind:href="link">click here</a> -->
  <!-- <a :href="link">click here</a> -->
<hr>
  <!-- <button v-on:click="toggleStatus">change status</button> -->
  <button @click="toggleStatus">change status</button>
</template>
