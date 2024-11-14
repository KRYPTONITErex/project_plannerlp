<template>
    <div class="friends">
      <div class="friend-info" >
        <div class="header" >
          <h3 id="info" @click="showDetail=!showDetail">{{ project.name }} =></h3>
          <div class="icon-container">
            <span class="material-icons" @click="deleteProject">delete</span>
            <span class="material-icons">edit</span>
            <span class="material-icons">check</span>
          </div>
        </div>
      </div>
  
      <div v-if="showDetail" class="location">
        <span><strong>Lives in:</strong> {{ project.liveIn }}</span>
        <span><strong>Works in:</strong> {{ project.workIn }}</span>
      </div>
      <br>
    </div>
  </template>
  
  <script>
  export default {
    props: ['project'],
    data() {
      return {
        showDetail: false,
        api: 'http://localhost:3000/myfriends/'
      };
    },
    methods: {
      deleteProject(){
        let deleteRoute = this.api+this.project.id;
        fetch(deleteRoute,{method:"DELETE"})
        .then(()=>{
            this.$emit('delete',this.project.id)
        })
        .catch((err)=>{
            console.log(err);
        })
        // console.log(this.api+this.project.id)
      }
    }
  };
  </script>
  
  <style>
  .friends {
  background-color: rgb(28, 97, 104);
  margin: 20px auto; /* Center horizontally */
  padding: 20px;
  border-radius: 15px;
  border-top-left-radius: 0px;
  border-bottom-right-radius: 5px;
  width: 500px;
  color: rgb(235, 247, 255);
  border-left: 10px solid #ff6201;
}
  
  .friend-info {
    text-align: left;
    padding-left: 20px;
  }
  
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .friend-info h3 {
    margin: 0;
    font-size: 1.2em;
  }
  
  .location, .work {
    color: rgb(249, 255, 255);
    padding: 10px;
  }
  
  strong {
    font-weight: bold;
  }
  
  .icon-container {
    display: flex;
    gap: 10px;
    color: rgb(255, 251, 223);
  }
  
  .material-icons {
    display: inline-flex;
    box-shadow: 1px 1px 0px 0px;
    border-radius: 15px 1px;
    padding: 5px;
  }

  .parent-container {
  display: flex;
  justify-content: center;
}

.material-icons:hover{
    color: rgb(250, 75, 75);
    cursor: pointer;
}

#info:hover{
    color: rgb(254, 85, 85);
    cursor: pointer;
}
  </style>