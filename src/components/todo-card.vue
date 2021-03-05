<template>
<section>
    <div class="top" id="todo-date">
    <h3 class="title">{{ currentDateTime() }}</h3>   
    <h3 class="topTitle">{{ topTitle }}</h3>
    <h3 class="title">{{count}} tâches</h3>
    </div>
<component-new-todo @sendTask="addTask"></component-new-todo>
<component-todo-list :tasktab="tasktab" @check="checkItems" @remove="removeItems"></component-todo-list>
</section>
</template>


<script>

import newTodoVue from './newTodo.vue';
import TodoListVue from './TodoList.vue';
export default {
    name: "App",
        el: '#todo-date',
        
   data(){
        return{
            count: 0,
            topTitle: "VueJs Tutorial ToDo List",
            tasktab : []
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
       this.tasktab.push(task);
    },
    checkItems(watch){
        if(watch.checked == false){
            watch.checked = true
            this.tasktab.indexOf(watch);
        }
        else{
            watch.checked = false
            this.tasktab.indexOf(watch);
        }

    },
    removeItems(watch){
        const die = this.tasktab.indexOf(watch);
        this.tasktab.splice(die, 1);
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
     max-width: 80%;
     display: block;
     margin: 0 auto;
     border-radius: 20px;
     margin-top: 25vh;
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
.topTitle {
    color: green;
    font-size: 25px;
}

</style>