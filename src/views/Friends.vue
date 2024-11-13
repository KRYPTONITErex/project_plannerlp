<template>
  <div>
    <h3>Friend lists</h3>
  </div>

  <div>
    <h3>colleagues lists</h3>
  </div>

    <div v-for="project in projects" :key="project.id">
        <FriComponent :project="project"></FriComponent>
    </div>

  
</template>



<script>
import FriComponent from '../components/FriComponent'
export default {
  components: { FriComponent },

  data(){
    return{
      projects: []
    };
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

<style>

</style>