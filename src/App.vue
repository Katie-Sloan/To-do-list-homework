<template>
  <div id="app">
    <form v-on:submit.prevent="saveNewItem">
      <label for="new-item">ToDo's:</label>
      <input id="new-item" type="text" v-model="newItem"/>
      <input type="submit" value="Save item"/>
    </form>

    <ul>
      <li v-for="(item, index) in items" :key="index" :class="item.isHighPriority ? 'high-priority':'low-priority'">
        <span>{{item.name}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      items: [
        {name: "Buy shopping", isHighPriority: true},
        {name: "Clean bathroom", isHighPriority: false},
        {name: "Car's MOT", isHighPriority: true}
      ],
      newItem: ""
    }
  },
  methods: {
    saveNewItem: function(){
      this.items.push({
        name: this.newItem,
        isHighPriority: false
      });
      this.newItem = "";
    }
  }  
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
