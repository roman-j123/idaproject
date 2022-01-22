<template>
  <ul class="cardlist" v-if="cards.length !== 0">
    <Card
      v-bind:card="card"
      v-for="card of cards"
      :key="card.id"
      @click="removeCard(card.id)"
    />
  </ul>
  <div class="cardlist-empty" v-else>
    <h2 class="cardlist-empty__header">Сейчас тут пусто :(</h2>
  </div>
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
.cardlist-empty {
  position: absolute;
  top: 50%;
  left: 50%;
  margin-right: -50%;
  transform: translate(-50%, -50%);
}
.cardlist-empty__header {
  margin: 0;
  font-size: 28px;
  line-height: 32px;
  color: rgba(255, 132, 132, 1);
}
</style>