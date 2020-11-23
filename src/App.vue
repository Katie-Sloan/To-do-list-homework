<template>
  <div id="app">
    <form v-on:submit.prevent="saveNewItem">
      <h1>ToDos</h1>
      <input type="text" v-model="newItem">
      <div>
        <div>
          <label for="High">High</label>
          <input type="radio" id="High" name="isPriority" v-bind:value="true" v-model="picked">
        </div>
        <div>
          <label for="Low">Low</label>
          <input type="radio" id="Low" name="isPriority" v-bind:value="false" v-model="picked">
        </div>
      </div>
      <input type="submit" value="Save item">
    </form>

    <ul>
      <li v-for="(item, index) in todos" :key="index" :class="item.isPriority ? 'high':'low'">
        <span>{{item.name}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      todos: [
        {name: "Buy shopping", isPriority: true},
        {name: "Clean bathroom", isPriority: false},  
        {name: "Car's MOT", isPriority: true} 
      ],
      newItem: ""
    }
  },
  methods: {
    saveNewItem: function(){
      this.todos.push({ 
        name: this.newItem,
        isPriority: this.picked
      });
      this.newItem = "";
    },
  },
}  

</script>

<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', 'sans-serif';
}

form {
  display: flex;
  flex-direction: row;
  margin: 20px 0;
  padding: 10px;
  justify-content: space-between;;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li.high {
  border: 2px solid #f2360c;
}

li.low {
  border: 2px solid #1a681e;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin: 5px;
  height: 10px;
  align-self: center;
}

button, input[type="submit"]{
  padding: 10px; 
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
  height: 40px;
  align-self: center;
}

</style>
