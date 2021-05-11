<template>
  <form>
    <div><input type="text" v-model.trim="searchText" /></div>
    <div class="btn">
      <button type="submit" @click.prevent="$emit('performSearch', searchText)">
        Cerca
      </button>
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
};
</script>

<style scoped>
</style>