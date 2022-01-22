<template>
  <header>
    <h2 class="app__title">{{ title }}</h2>
    <select v-model="selected" class="filter">
      <option
        v-for="option in options"
        :value="option.value"
        :key="option.value"
      >
        {{ option.text }}
      </option>
    </select>
  </header>
  <main class="container">
    <div class="container__addcard">
      <AddCard :add-card="addCard" />
    </div>
    <CardList :cards="cardsFiltered" :removeCard="removeCard" />
  </main>
</template>

<script>
import "normalize.css";
import CardList from "@/components/CardList";
import AddCard from "@/components/AddCard";
export default {
  name: "App",
  components: {
    CardList,
    AddCard,
  },
  data() {
    return {
      title: "Добавление товара",
      selected: "default",
      options: [
        { text: "По умолчанию", value: "default" },
        { text: "По возрастанию цены", value: "minToMax" },
        { text: "По убыванию цены", value: "maxToMin" },
      ],
      cards: [],
    };
  },
  created() {
    const cards = localStorage.getItem("cards");
    if (cards) this.cards = JSON.parse(cards);

    this.$watch(
      "cards",
      (value) => {
        localStorage.setItem("cards", JSON.stringify(value));
      },
      { deep: true }
    );
  },
  methods: {
    addCard(data) {
      data.id = this.max_id + 1;
      console.log(data);
      this.cards.push(data);
      console.log(this.cards);
    },
    removeCard(id) {
      if (confirm("Delete card ?")) {
        const index = this.cards.findIndex((el) => el.id === id);
        this.cards.splice(index, 1);
      }
    },
  },
  computed: {
    cardsFiltered() {
      switch (this.selected) {
        case "default": {
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          return this.cards.sort((a, b) => a.id - b.id);
        }
        case "minToMax": {
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          return this.cards.sort((a, b) => a.price - b.price);
        }
        case "maxToMin": {
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          return this.cards.sort((a, b) => b.price - a.price);
        }
        default: {
          return this.cards;
        }
      }
    },
    max_id() {
      if (this.cards.lenght === 0) return 1;
      return this.cards.reduce((max, el) => {
        return (max = el.id > max ? el.id : max);
      }, 0);
    },
  },
};
</script>

<style>
@font-face {
  font-family: "SourceSansPro";
  src: local("SourceSansPro"),
    url("./assets/fonts/SourceSansPro-Regular.ttf") format("trueType");
}
@font-face {
  font-family: "SourceSansPro-Bold";
  src: local("SourceSansPro-Bold"),
    url("./assets/fonts/SourceSansPro-Bold.ttf") format("trueType");
}
body {
  margin: 0;
  background-color: rgba(255, 254, 251, 0.8);
}
header {
  margin: 0 0 16px 0;
  display: flex;
  justify-content: space-between;
}
#app {
  margin: 0 auto;
  padding: 32px;
  max-width: 1440px;
  font-family: "SourceSansPro", Helvetica, Arial;
  font-size: 16px;
  line-height: 20px;
  color: #3f3f3f;
}
.app__title {
  margin: 0 0 16px 0;
  font-weight: 600;
  font-size: 28px;
  line-height: 32px;
  color: #3f3f3f;
}
.container {
  display: flex;
  box-sizing: border-box;
}
.container__addcard {
  margin: 0 0 0 0;
  width: 348px;
  flex-shrink: 0;
}
.filter {
  width: 121px;
  padding: 10px 16px;
  background-color: #fffefb;
  border: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  font-size: 12px;
  font-weight: 400;
  color: #b4b4b4;
  background-image: url("../src/assets/arrow.svg");
  background-repeat: no-repeat;
  background-position: center right 16px;
  border-radius: 4px;
  box-sizing: border-box;
  appearance: none;
  cursor: pointer;
}
@media screen and (max-width: 744px) {
  .container {
    flex-wrap: wrap;
  }
  .container__addcard {
    width: 100%;
    margin: 0 0 16px 0;
  }
}
</style>
