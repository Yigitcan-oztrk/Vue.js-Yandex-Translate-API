<template>
  <div class="container">
    <h1 class="text-center">Too-do List</h1>
    <h5 class="text-center">Vur.js İle Translator</h5>
    <br />
    <div class="row">
      <div class="col-md-12 text-center">
        <TranslateForm />

        <h3 class="text-succes text-center"></h3>
        <SearchHistory />
      </div>
    </div>
  </div>
</template>

<script>
import TranslateForm from "./components/TranlateForm.vue";
import SearchHistory from "./components/SearchHistory.vue";

export default {
  components: {
    TranslateForm,
    SearchHistory,
  },
  data() {
    return{

    }
  },
};
</script>
<style>
body{
  background-color: #dedede;
}
</style>