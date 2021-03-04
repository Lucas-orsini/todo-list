<template>
<section>
<header>
    <div class="top" id="todo-date">
    <h3 class="title">{{ currentDateTime() }}</h3>   
    <h3 class="top-title">Todo List</h3>
    <h3 class="title">{{count}}</h3>
    </div>
</header>
<component-new-todo @sendTask="addTask"></component-new-todo>
   
</section>
</template>


<script>
import newTodoVue from './newTodo.vue';
export default {
    name: "App",
        el: '#todo-date',
        
   data(){
        return{
            count: 0
            }
    },

  components: {
    'component-new-todo': newTodoVue,
  },

   methods: {
    currentDateTime() {
      const current = new Date();
      const tab_jour=new Array("Dimanche", "Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi");
      const date = tab_jour[current.getDay()] + ' ' +current.getDate()+'/'+(current.getMonth()+1);
      
      const dateTime = date;
      
      return dateTime;

   
    },
    addTask(a){
        console.log(a);
    }
    
  }
   
            
}




</script>
 
<style scoped>
    .content h3 {
        margin: 0;
        margin-top: 30px;
        margin-bottom: 30px;
    }
 section {
     background-color: #fff;
 }
 .top {
     display: flex;
     justify-content: space-around;
     border-bottom: rgba(128, 128, 128, 0.432) solid 1px;
 }

 .top-title{
     color: aquamarine;
    padding-left: 50px;
 }
.title {
    color:grey;
}



</style>