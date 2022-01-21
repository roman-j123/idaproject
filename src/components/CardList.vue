<template>
  <ul class="cardlist">
    <Card
      v-bind:card="card"
      v-on:removeCard="removeCard"
      v-for="(card, index) of cards"
      :key="index"
      :index="index"
    />
  </ul>
</template>

<script>
import Card from "@/components/Card";
export default {
  props: ["cards"],
  components: {
    Card,
  },
  methods: {
    removeCard(index) {
      this.$emit("removeCard", index);
    },
  },
};
</script>


<style scoped>
.cardlist {
  max-width: 1028px;
  min-width: 320px;
  padding: 0;
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(332px, 1fr));
  grid-gap: 16px;
}
</style>