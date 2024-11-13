<template>
  <div class="home">
 
    <h1> THIS is HOME VIEW , OK ?</h1>

    <div v-for="project in projects" :key="project.id">
        <FriComponent :project="project"></FriComponent>
    </div>

  </div>
</template>

<script>


import FriComponent from '../components/FriComponent'
export default {
  name: 'HomeView',
  components: {
    FriComponent,
    
  },
  data(){
    return{
      projects: []
    }
  },
  mounted(){
    fetch("http://localhost:3000/myfriends")
    .then((response)=>{
      return response.json();
    })
    .then((datas)=>{
      this.projects = datas
    })
    .catch((err)=>{
      console.log("Error Fetching data::", err)
    })
  }
}
</script>
