<template>
  <div>
    <h2>Calculator</h2>
    <input placeholder="num1" type="number" v-model.number="num1" />
    <select v-model="operand">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input placeholder="num2" type="number" v-model.number="num2" />
    <h2>{{ result }}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operand: "",
    };
  },
  /*eslint-disable */
  computed: {
    // Operand select
    result() {
      switch (this.operand) {
        case "+":
          return this.num1 + this.num2;
        case "-":
          return this.num1 - this.num2;
        case "*":
          return this.num1 * this.num2;
        case "/":
          return this.num1 / this.num2;
      }
    },
  },
  /*eslint-enable */
};
</script>

<style scoped>
input[type="number"] {
  border: 2px solid #ccc;
  border-radius: 4px;
  margin: 10px;
  padding: 10px;
  text-align: center;
  font-size: 16px;
}

select {
  padding: 10px 20px;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: #f1f1f1;
  font-size: 17px;
  font-weight: bold;
}
</style>