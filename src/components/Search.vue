<template>
  <form>
    <div><input type="text" v-model="searchText" /></div>
    <div class="btn">
      <button type="submit" @click.prevent="$emit('performSearch', searchText)">
        Cerca
      </button>
    </div>
    <div class="btn">
      <button type="reset" @click="resetSearch">Reset</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    resetSearch() {
      this.searchText = " ";
      $emit("performSearch", searchText);
    },
  },
};
</script>

<style scoped>
</style>