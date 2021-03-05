<template>
    

<div class="newTodo" v-for="items in tasktab" :key="items" :items="items"> 
    <input @click="check(items)" type="checkbox" name="done" id="checkbox"  v-model="checked" :key="items">
    <p :key="items" v-bind:class="{checked : items.checked}">{{items.taskName}}</p>
    <button type="button" name="delete" id="delete" :key="items" @click="remove(items)">X</button>
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
}
button {
    width: 40px;
    height: 40px;
    border-radius: 20px;
    outline-style: none;
    cursor:pointer;
    border: none;


}
input {
    width: 40px;
    height: 30px;
    
    


}
</style>