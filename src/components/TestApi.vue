<template>
  <div>
    <!-- Data API Example 1 -->
    <div class="my-5">
      <h2 class="mb-3">Get API Example #1</h2>
      <div class="row row-cols-1 row-cols-md-3 g-4">
        <div class="col" v-for="(card, index) in result1" :key="card.id">
          <div class="card">
            <img :src="card.avatar" class="avatar" />
            <div class="card-body">
              <h5 class="card-title">
                {{ fullname[index] }}
              </h5>
              <p class="card-text">
                {{ card.email }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- End -->

    <!-- Data API Example 2 -->
    <div class="my-5">
      <h2 class="mb-3">Get API Example #2</h2>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Employee Name</th>
            <th scope="col">Age</th>
            <th scope="col">Salary</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="table in result2" :key="table.id">
            <th scope="row">{{ table.id }}</th>
            <td>{{ table.employee_name }}</td>
            <td>{{ table.employee_age }}</td>
            <td>{{ table.employee_salary }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <!-- End -->
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      result1: [],
      result2: [],
    };
  },
  computed: {
    // Get fullname or Combine firstname and lastname from api
    fullname() {
      return this.result1.map((card) => {
        return card.first_name + " " + card.last_name;
      });
    },
  },

  methods: {
    // Fething Data APi Example 1
    async exampleOne() {
      await fetch("https://reqres.in/api/users")
        .then((res) => res.json())
        .then((res) => {
          console.log(res);
          this.result1 = res.data;
        });
    },

    // Get Data API with Axios Example 2
    async exampleTwo() {
      await axios
        .get("http://dummy.restapiexample.com/api/v1/employees")
        .then((res) => {
          console.log(res);
          this.result2 = res.data.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  mounted() {
    // Render Data from API when DOM mounting
    this.exampleOne();
    this.exampleTwo();
  },
};
</script>

<style>
.avatar {
  width: 150px;
  border-radius: 100px;
  margin: auto;
  margin-top: 15px;
}
</style>