<template>
<section>
<header>
    <div class="top" id="todo-date">
    <h3 class="title">{{ currentDateTime() }}</h3>   
    <h3 class="topTitle">{{ topTitle }}</h3>
    <h3 class="title">{{count}}</h3>
    </div>
</header>
<component-new-todo @sendTask="addTask"></component-new-todo>
<component-todo-list :tasktab="tasktab"></component-todo-list>
</section>
</template>


<script>
const tasktab = [];
import newTodoVue from './newTodo.vue';
import TodoListVue from './TodoList.vue';
export default {
    name: "App",
        el: '#todo-date',
        
   data(){
        return{
            count: 0,
            topTitle: "VueJs Tutorial ToDo List"
            }
    },

  components: {
    'component-new-todo': newTodoVue,
    'component-todo-list':TodoListVue
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
        let task ={
            taskName : a,
            checked : false
        }
       tasktab.push(task);
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
header {
    margin-top: 35vh;
}


</style>