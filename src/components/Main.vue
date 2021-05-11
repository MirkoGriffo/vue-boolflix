<template>
  <main>
    <Card v-for="item in films" :key="item.id" :info="item" />
  </main>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  name: "Main",
  components: {
    Card,
  },
  props: ["films"],
  data() {
    return {};
  },
};
</script>

<style scoped>
</style>