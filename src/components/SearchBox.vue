<template>
  <div class="container">
    <my-input v-model="searchQuery" placeholder="Search" />
  </div>
</template>

<script>
import MyInput from "./UI/MyInput.vue";
export default {
  name: "search-box",
  components: { MyInput },
  props: { updateSearchQuery: Function },
  data() {
    return {
      searchQuery: "",
    };
  },
  watch: {
    searchQuery() {
      this.updateSearchQuery(this.searchQuery);
    },
  },
};
</script>

<style lang="css" scoped>
.container {
  width: 200px;
  margin-top: 20px;
}
</style>
