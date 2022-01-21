<template>
  <header>
    <h2 class="app__title">{{ title }}</h2>
    <select v-model="selected" class="filter">
      <option
        v-for="option in options"
        v-bind:value="option.value"
        v-bind:key="option.value"
      >
        {{ option.text }}
      </option>
    </select>
  </header>
  <main class="container">
    <div class="container__addcard">
      <AddCard @add-card="addCard" />
    </div>
    <CardList v-bind:cards="cards" @removeCard="removeCard" />
  </main>
</template>

<script>
import "normalize.css";
import CardList from "@/components/CardList";
import AddCard from "@/components/AddCard";
export default {
  name: "App",
  data() {
    return {
      title: "Добавление товара",
      selected: "default",
      options: [
        { text: "По умолчанию", value: "default" },
        { text: "По возрастанию цены", value: "minToMax" },
        { text: "По убыванию цены", value: "maxToMin" },
      ],
      cards: [
        {
          title: "Наименование товара 1",
          link: "https://images.unsplash.com/photo-1642697318738-c74f8eac0bd0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          title: "Наименование товара 2",
          link: "https://images.unsplash.com/photo-1534353436294-0dbd4bdac845?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "11000",
        },
        {
          title: "Наименование товара 3",
          link: "https://images.unsplash.com/photo-1642698058508-ce2ef292cc13?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. ",
          price: "11100",
        },
        {
          title: "Наименование товара 4",
          link: "https://images.unsplash.com/photo-1638913662295-9630035ef770?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "11110",
        },
        {
          title: "Наименование товара 5",
          link: "https://images.unsplash.com/photo-1642682713988-8451d7fb6acf?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=764&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "11111",
        },
        {
          title: "Наименование товара 6",
          link: "https://images.unsplash.com/photo-1642683054267-cfc81c3a60de?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=689&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "21111",
        },
        {
          title: "Наименование товара 7",
          link: "https://images.unsplash.com/photo-1642682969825-09c60a60e989?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=642&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "22111",
        },
        {
          title: "Наименование товара 8",
          link: "https://images.unsplash.com/photo-1497215728101-856f4ea42174?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "22211",
        },
        {
          title: "Наименование товара 9",
          link: "https://images.unsplash.com/photo-1642616762342-e21f9eb2bf9e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "22221",
        },
      ],
    };
  },
  methods: {
    addCard(data) {
      this.cards.push(data);
      console.log(this.cards);
    },
    removeCard(index) {
      if (index !== -1) {
        this.cards.splice(index, 1);
      }
    },
  },
  components: {
    CardList,
    AddCard,
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
  font-family: "SourceSansPro", Helvetica, Arial;
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
