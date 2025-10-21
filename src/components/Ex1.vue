<template>
  <div>
    <p>x <input v-model.number="x" /></p>

    <select v-model="selectedOp" aria-label="operator-select">
      <option disabled value="">Choose</option>
      <option v-for="op in operators" :key="op" :value="op">{{ op }}</option>
    </select>

    <p>y <input v-model.number="y" /></p>

    <p>---------------------</p>
    <p>= {{ result }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      x: 0,
      y: 0,
      operators: ["+", "-", "*", "/", "%"],
      selectedOp: ""
    };
  },
  computed: {
    result() {
      switch (this.selectedOp) {
        case "+": return this.x + this.y;
        case "-": return this.x - this.y;
        case "*": return this.x * this.y;
        case "/": return this.y !== 0 ? this.x / this.y : "∞";
        case "%": return this.y !== 0 ? this.x % this.y : "NaN";
        default: return "";
      }
    }
  }
};
</script>

<style scoped>
p, input { font-family: monospace; }
p { white-space: pre; }
</style>
