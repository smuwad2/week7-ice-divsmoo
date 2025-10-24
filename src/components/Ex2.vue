<script>
export default {
  data() {
    return {
      items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
      newItem: ''               
    }
  },
  methods: {
    addItem() {
      if (!this.newItem || !this.newItem.trim()) return;
      this.items.push(this.newItem.trim()); 
      this.newItem = '';                   
    }
  }
}
</script>

<template>
  <h2>Shopping Cart</h2>

  <ul>
    <li v-for="(item, idx) in items" :key="idx">
      {{ item }}
      <button @click="items.splice(idx, 1)">Delete!</button>
    </li>
  </ul>

  <input type="text" v-model="newItem" placeholder="New item" />
  <button @click="addItem">Add!</button>
</template>

