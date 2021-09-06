<template>
  <div class="container">
    <h1 class="text-center">Too-do List</h1>
    <h5 class="text-center">Vur.js Weather</h5>
    <br />
    <div class="row">
      <div class="col-md-12 text-center">
        <TranslateForm />
    <br />
        <h5 class="text-succes text-center">Corona result</h5>
    <br />
        <CoronaResult />
      </div>
    </div>
    
  </div>
</template>

<script>
import TranslateForm from "./components/TranlateForm.vue";
import SearchHistory from "./components/SearchHistory.vue";
import CoronaResult from "./components/CoronaResult.vue";
export default {
  components: {
    TranslateForm,
    SearchHistory,
    CoronaResult,
  },
  data() {
    return {};
  },
};
</script>
<style>
body {
  background-color: #dedede;
}
</style>