<template>
  <header>
    <h2 class="app__title">{{ title }}</h2>
  </header>
  <main class="container">
    <div class="container__addcard">
      <AddCard />
    </div>
    <CardList v-bind:cards="cards" />
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
      cards: [
        {
          id: 1,
          title: "Наименование товара 1",
          link: "https://images.unsplash.com/photo-1642697318738-c74f8eac0bd0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 2,
          title: "Наименование товара 2",
          link: "https://images.unsplash.com/photo-1534353436294-0dbd4bdac845?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "11000",
        },
        {
          id: 3,
          title: "Наименование товара 3",
          link: "https://images.unsplash.com/photo-1642698058508-ce2ef292cc13?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. ",
          price: "11100",
        },
        {
          id: 4,
          title: "Наименование товара 4",
          link: "https://images.unsplash.com/photo-1638913662295-9630035ef770?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "11110",
        },
        {
          id: 5,
          title: "Наименование товара 5",
          link: "https://images.unsplash.com/photo-1642682713988-8451d7fb6acf?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=764&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "11111",
        },
        {
          id: 6,
          title: "Наименование товара 6",
          link: "https://images.unsplash.com/photo-1642683054267-cfc81c3a60de?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=689&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "21111",
        },
        {
          id: 7,
          title: "Наименование товара 7",
          link: "https://images.unsplash.com/photo-1642682969825-09c60a60e989?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=642&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "22111",
        },
        {
          id: 8,
          title: "Наименование товара 8",
          link: "https://images.unsplash.com/photo-1497215728101-856f4ea42174?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "22211",
        },
        {
          id: 9,
          title: "Наименование товара 9",
          link: "https://images.unsplash.com/photo-1642616762342-e21f9eb2bf9e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "22221",
        },
      ],
    };
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
  width: 348px;
  flex-shrink: 0;
}
</style>
