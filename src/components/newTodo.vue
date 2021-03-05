
<!-- affichage de new todo-->
<template>
  <div class="search">
    <input type="text" v-model="taskName" placeholder="Nouvelle tâche..." />
    <button type="submit" @click="NewTask()">
      <i class="fas fa-plus"></i>
    </button>
  </div>
</template>

<script>
export default {
  el: ".search",

  // donnée
  data() {
    return {
      taskName: "",
    };
  },

  //notre fonction
  methods: {
    //verification input vide
    NewTask() {
      if (this.taskName != "") {
        //envoie des données a todocard
        this.$emit("sendTask", this.taskName);
        //on vide l'input
        this.taskName = "";
      }
    },
  },
};
</script>

<style scoped>
.search {
  background-color: #fff;
  display: flex;
  justify-content: center;
  margin-top: 20px;
  padding-bottom: 5vh;
}
.search input {
  border: none;
  border-bottom: solid green;
  outline-style: none;
  font-size: 20px;
}
button {
  margin-left: 20px;
  border: none;
  border-radius: 30px;
  background-color: green;
  color: #fff;
  outline-style: none;
  cursor: pointer;
  width: 40px;
  height: 40px;
}
</style>
