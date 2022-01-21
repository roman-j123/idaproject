<template>
  <li class="cardlist__item card">
    <button
      class="card__delete"
      v-on:click="$emit('removeCard', this.index)"
    ></button>
    <img v-bind:src="card.link" v-bind:alt="card.title" class="card__img" />
    <div class="card__container">
      <h2 class="card__title">{{ card.title }}</h2>
      <p class="card__text">
        {{ card.description }}
      </p>
      <span class="card__price">{{ card.price }} руб.</span>
    </div>
  </li>
</template>

<script>
export default {
  props: ["card", "index"],
};
</script>

<style scoped>
.cardlist__item {
  position: relative;
  margin: 0 0 16px 0;
  max-width: 332px;
  width: 100%;
  height: 423px;
  box-sizing: border-box;
}
.card {
  background-color: rgba(255, 254, 251, 1);
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}
.card:hover {
  cursor: pointer;
}
.card__container {
  padding: 0 16px 24px;
  display: flex;
  flex-direction: column;
  height: 223px;
  box-sizing: border-box;
}
.card__img {
  height: 200px;
  width: 100%;
  display: block;
  background-color: #3f3f3f;
  object-fit: cover;
  border-radius: 4px 4px 0px 0px;
}
.card__title {
  margin: 16px 0;
  font-family: "SourceSansPro", Helvetica, Arial;
  font-weight: 600;
  font-size: 20px;
  line-height: 25px;
}
.card__text {
  margin: 0;
}
.card__price {
  margin: auto 0 0 0;
  font-size: 24px;
  font-weight: 600;
  line-height: 30px;
}
.card__delete {
  padding: 0;
  display: none;
  position: absolute;
  top: -8px;
  right: -8px;
  width: 32px;
  height: 32px;
  border: none;
  background-image: url("../assets/basket.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-color: rgba(255, 132, 132, 1);
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  cursor: pointer;
  transition: 0.3s;
}
.card__delete:hover {
  background-color: rgb(176, 91, 91);
}
.card:hover .card__delete {
  display: block;
}
</style>

