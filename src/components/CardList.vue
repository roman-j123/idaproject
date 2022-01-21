<template>
  <ul class="cardlist">
    <Card
      v-bind:card="card"
      v-for="card of cards"
      :key="card.id"
      @click="removeCard(card.id)"
    />
  </ul>
</template>

<script>
import Card from "@/components/Card";
export default {
  props: {
    cards: Array,
    removeCard: Function,
  },
  components: {
    Card,
  },
};
</script>


<style scoped>
.cardlist {
  max-width: 1028px;
  min-width: 320px;
  margin: 0 0 0 0;
  padding: 0;
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(332px, 1fr));
  grid-gap: 16px;
}
</style>