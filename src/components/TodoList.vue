<template>
    

<div class="newTodo" v-for="items in tasktab" :key="items" :items="items"> 
<div class="round">
    <input @click="check(item)" type="checkbox" name="done" id="checkbox"  v-model="checked" :key="items">
     <label for="checkbox"></label>
     </div>
    <p v-bind:class="{'checked' : items.checked}">{{items.taskName}}</p>
    <button type="button" name="delete" id="delete" :key="items" @click="remove(items)"><i class="fas fa-trash fa-2x"></i></button>
    </div>
</template>

<script>
export default {
    props : {
        tasktab: {
            type : Array
        }
    },
    methods :{
        check(watch) {
            this.$emit('check', watch)
        },
          remove(watch) {
            this.$emit('remove', watch)
        }
    }
    }

</script>

<style scoped>
.newTodo {
    background-color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 45px;
}
.newTodo p {
    margin-right: 80vh;
    margin-left: 5vh;
    font-size: 30px;
    width: 100px;
}
button {
    width: 50px;
    height: 50px;
    border-radius: 30px;
    outline-style: none;
    cursor:pointer;
    border: none;
    background-color: red;
}
button i{
    color: #fff;
}




.round {
  position: relative;
}

.round label {
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 50%;
  cursor: pointer;
  height: 28px;
  left: 0;
  position: absolute;
  top: 0;
  width: 28px;
}

.round label:after {
  border: 2px solid #fff;
  border-top: none;
  border-right: none;
  content: "";
  height: 6px;
  left: 7px;
  opacity: 0;
  position: absolute;
  top: 8px;
  transform: rotate(-45deg);
  width: 12px;
}

.round input[type="checkbox"] {
  visibility: hidden;
}

.round input[type="checkbox"]:checked + label {
  background-color: #66bb6a;
  border-color: #66bb6a;
}

.round input[type="checkbox"]:checked + label:after {
  opacity: 1;
}



















</style>