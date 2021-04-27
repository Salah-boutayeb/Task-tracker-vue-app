<template>
  <header>
      <h1>{{title}}</h1>
      <Button  @toggle-form="$emit('toggle-form')" :color="!showStatOfFrom ? 'green':'red'" :text="!showStatOfFrom ? 'Add Task':'close'"/>
  </header>
</template>

<script>
import Button from "./button";
export default {
    name: 'Header',
    props:{
        title: String,
        showStatOfFrom:Boolean
    },
    components:{
        Button
    },
    methods:{
        
    }
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-around;
    color: rgb(108, 227, 248);

}

</style>
