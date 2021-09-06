<template>
  <div class="container">
    <div class="input-group mb-3">
      <span class="input-group-text" id="basic-addon1">Filitre</span>
      <input
        type="text"
        v-model="search"
        class="form-control"
        placeholder="Username"
        aria-label="Username"
        aria-describedby="basic-addon1"
      />
    </div>
    <table class="table table-dark table-striped">
      <thead>
        <tr>
          <th scope="col">Ülke</th>
          <th scope="col">Toplam Test</th>
          <th scope="col">Toplam Vefat</th>
          <th scope="col">Toplam İyileşen</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="infos in info" key="infos.[]">
          <td>{{ infos.country }}</td>
          <td>{{ infos.totalCases }}</td>
          <td>{{ infos.totalDeaths }}</td>
          <td>{{ infos.totalRecovered }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>


<script>
import axios from "axios";
export default {
  data() {
    return {
      info: [],
      search: "",
    };
  },
  methods: {},
  mounted() {
    axios
      .get("https://api.collectapi.com/corona/countriesData", {
        headers: {
          Authorization: "apikey 0SqN7rZI2rmDGyfMrWGuS9:26EubLZxIVmmf1lOEiYWCs",
          Content: "text/plain; charset=utf-8",
        },
      })
      .then((cor) => {
        console.log(cor.data);
        this.info = cor.data.result;
      })
      .catch((error) => {
        console.error(error);
      });
  },
  computed: {
    filteredList() {
      return this.info.itemList.filter((i) => i.includes(this.search));
    },
  },
};
</script>




<style scoped>
</style>