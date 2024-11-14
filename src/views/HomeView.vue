<template>
  <div class="home">
 
    <h1> THIS is HOME VIEW , OK ?</h1>

    <div v-for="project in projects" :key="project.id" >
        <FriComponent :project="project" @delete="deleteProj"></FriComponent>
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
  },
  methods:{
    deleteProj(id){
      this.projects=this.projects.filter(project=>{
        return project.id!=id;
      })
    }
  }
}
</script>
