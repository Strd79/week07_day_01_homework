<template>
  <div id="app">
    <h1>David's To Do List</h1>
    <form v-on:submit.prevent="saveNewToDoItem">
      <label for="new-toDoItem">Add a new item to do:</label>
      <input type="text" id="new-toDoItem" v-model="newToDoItem.name">
      <label for="high">High</label>
      <input type="radio" name="priority" id="high" value="high" v-model="newToDoItem.priority" required>
      <label for="low">Low</label>
      <input type="radio" name="priority" id="low" value="low" v-model="newToDoItem.priority">
      <input type="submit" value="Save to list">
    </form>
    <ul>
      <li v-for="(item, index) in toDoItems" :key="index" :class="item.priority">
        <span>{{ item.name }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  data() {
    return {
      toDoItems: [
        {name: "Water plants", priority: "low"},
        {name: "Get Milk", priority: "high"},
        {name: "Book dentist appointment", priority: "high"},
      ],
      newToDoItem: {
        name: "",
        priority: null
      },
    };
  },
  methods: {
    saveNewToDoItem: function() {
      this.toDoItems.push(this.newToDoItem);
      this.newToDoItem = {
        name: "",
        priority: null
      };
    }
  }
}
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

li {
  margin: auto;
  margin-top: 10px;
  padding: 4px 0;
  width: 400px;
  
}

li.low{
  border: 2px solid green;
}

li.high{
  border: 2px solid red;
  color: darkred;
}

ul {
  list-style: none;
  margin-top: 30px;
  padding: 0;
}

input[type=text] {
  margin-left: 10px;
  width: 250px;
  height: 30px;
  box-sizing: border-box;
}

input[type=submit] {
  margin-left: 10px;
  background-color: darkcyan;
  color: white;
  height: 30px;
  width: 90px;
  box-sizing: border-box;
}

label {
  margin-left: 10px;
}

</style>
