<template>
  <div id="app">
    <form v-on:submit.prevent="saveNewItem">
      <label for="new-item">ToDos:</label>
      <input id="new-item" type="text" v-model="newItem"/>
      <input type="submit" value="Save item"/>
    </form>

    <ul>
      <!-- <li v-for="(item, index) in todos" :key="index" :class="item.isHighPriority ? 'high-priority':'low-priority'"> -->
      <li v-for="(item, index) in todos">
        <span>{{item}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      todos: [
        "Buy shopping", "Clean bathroom", "Car's MOT"
      ],
      newItem: ""
    }
  },
  methods: {
    saveNewItem: function(){
      this.todos.push(this.newItem) 
        // name: this.newItem,
        // isHighPriority: false
      this.newItem = "";
    }
  },
}  

</script>

<style>
li.high-priority {
  border: 2px solid #f2360c;
}

li.low-priority {
  border: 2px solid #1a681e;
}
</style>
