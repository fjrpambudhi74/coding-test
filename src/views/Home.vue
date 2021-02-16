<template>
  <div class="home">
    <div>
      <h2>Class and Style Binding</h2>
      <div
        @click="changeColor(boxSelected)"
        :class="[boxSelected ? 'red' : 'blue']"
        class="box"
      >
        <h3 class="clickme">Click Me!</h3>
      </div>
    </div>
    <hr />
    <div>
      <h2>Components with props</h2>
      <ul>
        <nested-component
          v-for="item in items"
          :key="item.id"
          :item="item"
        ></nested-component>
      </ul>
      <hr />
    </div>
    <calculator></calculator>
    <hr />
    <data-table></data-table>
    <hr />
    <test-api></test-api>
    <hr />
    <local-storage></local-storage>
  </div>
</template>

<script>
import NestedComponent from "../components/NestedComponent.vue";
import DataTable from "../components/DataTable.vue";
import TestApi from "../components/TestApi.vue";
import Calculator from "../components/Calculator.vue";
import LocalStorage from "../components/LocalStorage.vue";

export default {
  name: "Home",
  components: {
    NestedComponent,
    DataTable,
    TestApi,
    Calculator,
    LocalStorage,
  },
  data() {
    return {
      boxSelected: false,
      items: [
        { id: 1, title: "Frontend Engineers", desc: "This is body" },
        { id: 2, title: "Backend Engineers", desc: "This is body" },
      ],
    };
  },

  methods: {
    changeColor(value) {
      this.boxSelected = !value;
    },
  },
};
</script>

<style scoped>
.box {
  width: calc(100% - 32px);
  height: 100px;
  margin: 16px;
  border: 2px dashed #ccc;
}

.red {
  border-color: red;
  background-color: salmon;
}

.blue {
  border-color: blue;
  background-color: lightblue;
}

.clickme {
  margin-top: 30px;
}

ul {
  list-style: none;
  margin: 2rem auto;
  padding: 0;
  max-width: 50rem;
}
</style>
