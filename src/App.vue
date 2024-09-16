<script>
export default {
  data() {
    return {
      name: "lido",
      status: "pending",
      tasks:['learn vue', 'learn nuxt', 'learn dockeer'],
      link: 'https://google.com' 
    };
  },
  methods:{
    toggleStatus(){
      if(this.status === 'active'){
        this.status = 'pending'
      }else if(this.status === 'pending'){
        this.status = 'inactive'
      }else{
        this.status = 'active'
      }
    }
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
  <a :href="link">click here</a>
<hr>
  <!-- <button v-on:click="toggleStatus">change status</button> -->
  <button @click="toggleStatus">change status</button>
</template>
