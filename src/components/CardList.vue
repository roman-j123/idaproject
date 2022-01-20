<template>
  <ul class="cardlist">
    <Card v-bind:card="card" v-for="card of cards" :key="card.id" />
  </ul>
</template>

<script>
import Card from "@/components/Card";
export default {
  props: ["cards"],
  components: {
    Card,
  },
};
</script>


<style scoped>
.cardlist {
  width: 1028px;
  margin: 0 0 0 auto;
  padding: 0;
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>