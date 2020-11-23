<template>
  <div id="app">
    <form v-on:submit.prevent="saveNewItem"></form>
      <label for="new-item">Add a new item: </label>
      <input id="new-item" type="text" v-model="newItem"/>
      <input type="submit" value="Save new item"/>
    </form>

    <ul>
      <li v-for="(item.index) in items" 
      :key="index"
      :class="item.isHighPriority ? 'high-priority':'low-priority'"
        <span>{{item.name}}</span>
      </li>
    </ul>
  </div>
</template>

<style>
li.high-priority {
  border: 2px solid #f2360c;
}

li.low-priority {
  border: 2px solid #1a681e;
}
</style>
