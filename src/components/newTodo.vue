

<template>
      <div class="search">
        <input type="text" v-model="taskName">
        <button type="submit" @click="NewTask()"> + </button>
    </div>
</template>

<script>
export default {
    el:'.search',
    data(){
        return{
            taskName : "",
        }
    },
    methods:{
        //   taskCount(){
        //     this.count++
            
        // },
        NewTask() {
            if(this.taskName != "") {
                this.$emit('sendTask', this.taskName)
                this.taskName = ""
            }
    }
    

}
}
</script>

<style scoped>
.search {
    background-color: #fff;
     display: flex;
    justify-content: center;
}
</style>
