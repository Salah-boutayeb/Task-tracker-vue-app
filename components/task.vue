<template>
<div @dblclick="toggel()" :class="[task.reminder ? 'reminder':'','task' ]">
    <h3>{{task.text}}
        <em @click="remove(task.id)" class="fas fa-times"></em>
    </h3>
    <hr>
    <p>{{task.day}}</p>
    
</div>
  
</template>

<script>
export default {
    name:'Task',
    props:{
        task:Object,
    },
    methods:{
        toggel(){
            this.task.reminder=!this.task.reminder
        },
        remove(id){
            this.$emit('delete-task',id)
        }
    }

}
</script>

<style scoped>
.task{
    background:#F4F4F4;
    margin: 8PX;
    padding: 10px 20PX;
    border-radius: 8px;
    border: 2px solid steelblue;
    cursor: pointer;

}
hr{
    width: 26ch;
    
}
.task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.reminder{
    border-left: 6px solid rgb(115, 255, 102) ;
}
.fas{
    color: red;
}

</style>