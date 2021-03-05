<template>
    

<div class="newTodo" v-for="items in tasktab" :key="items" :items="items"> 
<div class="round">
    <input @click="check(item)" type="checkbox" name="done" id="checkbox"  v-model="checked" :key="items">
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


#checkbox {
    width: 1.3em;
    height: 1.3em;
    background-color: white;
    border-radius: 50%;
    vertical-align: middle;
    border: 1px solid #ddd;
    -webkit-appearance: none;
    outline: none;
    cursor: pointer;
}

#checkbox:checked {
    background-color: green;
}





















</style>