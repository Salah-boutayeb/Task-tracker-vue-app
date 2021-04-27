<template>
  <div class="container">
    <Header :showStatOfFrom="showAddTask" @toggle-form="formToggler()" title="</ Task tracker" />
    <div v-if="showAddTask">
       <add-task @addTask="addTask"/>
    </div>
    <Tasks @delete-task="delete" 
            :tasks="tasks"/>
    
  </div>

</template>

<script>
import AddTask from './components/AddTask.vue';
import Button from './components/button';
import Header from "./components/Header";
import Tasks from "./components/tasks";

export default {
  
  name: 'App',
  components:{
    Header,
    Tasks,
    Button,
    AddTask
  },
  data(){
    return {
      tasks:[],
      showAddTask:false,
  }
  },
  created(){
    this.tasks=[
      {
        id:1,
        text:'task one',
        day: 'day one',
        reminder: true
      },
      {
        id:2,
        text:'task two',
        day: 'day two',
        reminder: true
      },
      {
        id:3,
        text:'task three',
        day: 'day three',
        reminder: false
      },
    ]
  },
  methods:{
    addTask(task){
      this.tasks=[...this.tasks,task]
    },
    delete(id){
      if(confirm('are you sure you wanna delete this task'))
      this.tasks= this.tasks.filter((task)=> task.id !==id)
      
    },
    formToggler(){
            this.showAddTask=!this.showAddTask
        }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 100px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  
  
  
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 8px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:active {
  transform: scale(0.68);
}
.btn:hover {
  color: #000;
  background: #fff;
  border:1PX SOLID  #000 ;
  padding: 10px 22px;
  
  
}
.btn-block {
  display: block;
  width: 50%;
  margin: 0 auto;

}

</style>
