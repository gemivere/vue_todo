<template>
  <button id="newList" @click="makeList">New List</button>
  <button id="deleteList" @click="deleteList">Delete List</button>
  <select name="listSelector" id="listSelector">
    <option v-for="(list, index) in allLists" :key="index">{{ list }}</option>
  </select>
</template>

<script>
//import func from "vue-editor-bridge"

export default {
  name: "Lists",
  components: {},
  data() {
    return {
      allLists: ["default"],
    };
  },
  methods: {
    makeList: function () {
      let newList = prompt("Please enter the name of your list:", "");
      if (newList != null && newList != "") {
        if (this.allLists.indexOf(newList) < 0) {
          this.allLists.push(newList);
        } else {
          alert("This list already exists.");
        }
      }
    },
    deleteList: function () {
      let badList = prompt(
        "Please enter the name of the list you wish to delete:",
        ""
      );
      if (badList != null && badList != "") {
        if (this.allLists.length <= 1) {
          if (badList in this.allLists) {
            this.allLists.pop(badList);
          } else {
            alert("list ${badList}");
          }
        } else {
          alert("You cannot delete your last list.");
        }
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
