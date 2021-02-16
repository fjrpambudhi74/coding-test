<template>
  <div class="container">
    <h2 class="my-4">Data Table</h2>
    <!-- Render Data Table using vue-table-2 with filter, sorting & pagination -->
    <v-client-table :data="tableData" :columns="columns" :options="options">
    </v-client-table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      // vue-table-2
      columns: ["id", "name", "album"],
      tableData: [],
      options: {
        headings: {
          id: "ID",
          name: "Song Name",
          album: "Album",
        },
        sortable: ["id", "name", "album"],
        filterable: ["name", "album"],
        perPage: 5,
        perPageValues: [3, 5, 10],
        orderBy: { column: "id" },
        pagination: { chunk: 3, dropdown: false },
      },
    };
  },
  mounted() {
    // Get Data from Json server
    axios.get("http://localhost:4000/songs").then((res) => {
      console.log(res);
      this.tableData = res.data;
    });
  },
};
</script>

<style >
label {
  float: left;
  margin-top: 7px;
  margin-right: 10px;
}

.VueTables__search {
  float: left;
}

.VueTables__limit {
  float: right;
}

.VuePagination {
  justify-content: center;
}

.VuePagination__pagination-item {
  padding: 5px !important;
  border-radius: 8px;
  margin: 5px;
}

.page-link {
  border: none !important;
}

.page-item.active .page-link {
  border-radius: 5px !important;
}
</style>