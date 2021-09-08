<template>
<div class="container">
  <div style="display: flex; align-items: center; max-width: 150px !important;" >
    <div class="card mr-3" style="width: 18rem" v-for="eczs in ecz">
      <div class="card-header">{{eczs.name}}</div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">{{eczs.phone}}</li>
        <li class="list-group-item">{{eczs.dist}}</li>
        <li class="list-group-item">{{eczs.address}}</li>
      </ul>
    </div>
  </div>
  </div>
</template>



<script>
import axios from "axios";
export default {
  data() {
    return {
    ecz:[],
    };
  },
  methods: {},
  mounted() {
    axios
      .get("https://api.collectapi.com/health/dutyPharmacy?&il=Bursa", {
        headers: {
          Authorization: "apikey 0SqN7rZI2rmDGyfMrWGuS9:26EubLZxIVmmf1lOEiYWCs",
          Content: "text/plain; charset=utf-8",
        },
      })
      .then((ecz) => {
        console.log(ecz.data);
        this.ecz = ecz.data.result    
      })
      .catch((error) => {
        console.error(error);
      });
  },
};
</script>

<style>

</style>