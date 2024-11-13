<template>
    <div class="friends">
      
        <div class="friend-info" @click="showDetail=!showDetail">
        <h3>{{ project.name }} =></h3>
       
        <div v-if="showDetail">
        <div class="location">
          <span><strong>Lives in:</strong> {{ project.liveIn }}</span>
        
          <span><strong>Works in:</strong> {{ project.workIn }}</span>
        </div>
        </div>

      </div>

    </div>
  </template>
  
  <script>
  export default {
    props: ['project'],
    props: ['project'],
    data(){
        return{
            showDetail: false
        }
    }
  }
  </script>
  
  <style>
  .friends {
    background-color: crimson;
    margin: 20px;
    padding: 20px;
    border-radius: 15px;
    width: 300px;
    cursor: pointer;
    color: bisque;
    
  }
  
  .friend-info {
    display: flex;
    flex-direction: column;
    text-align: left;
    padding-left: 20px;
  }
  
  .friend-info h3 {
    margin: 0;
    font-size: 1.2em;
  }
  
  .location, .work {
    margin-top: 5px;
    color: azure;
  }
  
  strong {
    font-weight: bold;
  }
  
  </style>