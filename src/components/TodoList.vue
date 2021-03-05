<template>
    

<div class="newTodo" v-for="items in tasktab" :key="items" :items="items"> 
    <input type="checkbox" name="done" id="checkbox" v-model="checked" :key="items">
    <p :key="items">{{items.taskName}}</p>
    <input type="button" name="delete" id="delete" :key="items">
    </div>
</template>

<script>
export default {
    props : {
        tasktab: {
            type : Array
        }
    },
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
</style>