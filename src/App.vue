<script>
import { ref } from 'vue';
export default {
  setup(){
    const name =ref('lido');
    const status=ref('active');
    const tasks=ref(['task1','task2', 'task3', 'task4']);
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
    return {name,status,tasks,toggleStatus}
  }
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status==='active'">user is active</p>
  <p v-else-if="status==='pending'">user is pending</p>
  <p v-else=>user is not active</p>


  <h3>tasks</h3>
  <ul>
    <li  v-for="task in tasks" :key="task">{{ task }}

    </li>
  </ul>
  <!-- <a v-bind:href="link">click here</a> -->
  <!-- <a :href="link">click here</a> -->
<hr>
  <!-- <button v-on:click="toggleStatus">change status</button> -->
  <button @click="toggleStatus">change status</button>
</template>
