<template>
  <form @submit="onSubmit" class="add-form">

      <div class="form-control">
          <label for="">Task:</label>
          <input type="text" placeholder="Add Task" v-model="text">
      </div>
      <div class="form-control">
          <label for="">Date & Time:</label>
          <input type="text" placeholder="Add Date & Time" v-model="day">
      </div>
      <div class="form-control form-control-check">
          <label for="">set reminder:</label>
          <input type="checkbox" placeholder="Add Task" v-model="reminder">
        </div>
        <input type="submit" value="save task" class="btn btn-block">
  </form>
</template>

<script>
export default {
    name:"AddTask",
    data(){
        return {
            text:"",
            day:"",
            reminder:false
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()

            if (!this.text) {
                alert('add a task')
                return
            }

            const newTask={
                id:Math.floor(Math.random()*100),
                text:this.text,
                day:this.day,
                reminder:this.reminder
            }
            this.$emit('addTask',newTask)
            this.text=""
            this.day=""
            this.reminder=false

        }
    }

}
</script>

<style >
.add-form{
    margin-bottom: 40px;
    
}
.form-control{
    
    margin: 20px 0;
}
.form-control label{
    text-align: center;
    font-weight:bold ;
    font: 900PX;
    
}
.form-control input{
    display: block;
    width: 100%;
    height: 40px;
}
.form-control-check input{
    display: inline;
    width: 30px;
    height: 30px;
    
}
.form-control-check{
    display: flex;
    justify-content: space-between;
}
</style>