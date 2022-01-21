<template>
  <div class="addcard">
    <form
      method="POST"
      class="addcard__form"
      novalidate="true"
      @submit="checkForm"
    >
      <div class="addcard__block">
        <div class="addcard__label">
          <label for="card-name" class="addcard__title"
            >Наименование товара</label
          >
          <span class="addcard__required"></span>
        </div>
        <input
          class="addcard__input"
          type="text"
          minlength="5"
          maxlength="25"
          id="card-name"
          v-model="newCard.title"
          @input="checkInput('title')"
          placeholder="Введите наименование товара"
        />
        <p class="addcard__error" v-if="isValidName">{{ errorMessage }}</p>
      </div>
      <div class="addcard__block">
        <label for="card-description" class="addcard__title"
          >Описание товара</label
        >
        <textarea
          class="addcard__input addcard__input_description"
          type="text"
          maxlength="200"
          id="card-description"
          v-model="newCard.description"
          placeholder="Введите описание товара"
        ></textarea>
      </div>
      <div class="addcard__block">
        <div class="addcard__label">
          <label for="card-href" class="addcard__title"
            >Ссылка на изображение товара</label
          >
          <span class="addcard__required"></span>
        </div>
        <input
          class="addcard__input"
          type="url"
          id="card-href"
          v-model="newCard.link"
          @input="checkInput('link')"
          placeholder="Введите ссылку"
        />
        <p class="addcard__error" v-if="isValidLink">{{ errorMessage }}</p>
      </div>
      <div class="addcard__block">
        <div class="addcard__label">
          <label for="card-price" class="addcard__title">Цена товара</label>
          <span class="addcard__required"></span>
        </div>
        <input
          class="addcard__input"
          type="number"
          id="card-price"
          v-model="newCard.price"
          @input="checkInput('price')"
          placeholder="Введите цену"
        />
        <p class="addcard__error" v-if="isValidPrice">{{ errorMessage }}</p>
      </div>
      <button type="submit" class="addcard__button" :disabled="!isValid">
        Добавить товар
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      defaulCard: {
        title: "",
        description: "",
        link: "",
        price: null,
        id: null,
      },
      newCard: {},
      isValidName: false,
      isValidLink: false,
      isValidPrice: false,
      errorMessage: "Поле является обязательным",
    };
  },
  props: {
    addCard: Function,
  },
  created() {
    this.newCard = JSON.parse(JSON.stringify(this.defaulCard));
  },
  methods: {
    checkInput(fieldName) {
      switch (fieldName) {
        case "title":
          {
            this.isValidName = this.newCard.title ? false : true;
          }
          break;
        case "link":
          {
            this.isValidLink = this.newCard.link ? false : true;
          }
          break;
        case "price":
          {
            this.isValidPrice = this.newCard.price ? false : true;
          }
          break;
      }
    },
    checkForm(event) {
      event.preventDefault();
      console.log(this.newCard);
      this.addCard(this.newCard);

      this.newCard = JSON.parse(JSON.stringify(this.defaulCard));
    },
  },
  computed: {
    isValid() {
      return this.isValidName && this.isValidLink && this.isValidPrice;
    },
  },
};
</script>

<style scoped>
.addcard {
  position: fixed;
  padding: 24px;
  margin: 0 16px 0 0;
  max-width: 332px;
  width: 100%;
  height: 440px;
  background-color: rgba(255, 254, 251, 1);
  border-radius: 4px;
  box-sizing: border-box;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
}
.addcard__form {
  width: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
.addcard__error {
  position: absolute;
  bottom: -18px;
  margin: 0;
  font-size: 8px;
  color: rgba(255, 132, 132, 1);
}
.addcard__block {
  position: relative;
  margin: 0 0 18px 0;
}
.addcard__label {
  display: flex;
}
.addcard__title {
  margin: 0 0 4px 0;
  font-size: 10px;
  font-weight: 400;
  line-height: 12px;
}
.addcard__input {
  padding: 10px 16px;
  width: 100%;
  font-size: 12px;
  line-height: 15px;
  color: #3f3f3f;
  border: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  box-sizing: border-box;
}
.addcard__input:last-child {
  margin: 0 0 0 0;
}
.addcard__input_description {
  height: 108px;
  resize: none;
  font-family: "SourceSansPro", Helvetica, Arial;
  font-size: 12px;
  font-weight: 400;
  line-height: 15px;
  color: #3f3f3f;
}
.addcard__input_description::-webkit-input-placeholder,
.addcard__input_description:-moz-placeholder,
.addcard__input_description::-moz-placeholder,
.addcard__input_description:-ms-input-placeholder,
.addcard__input::placeholder {
  font-size: 12px;
  font-weight: 400;
  line-height: 15px;
  color: #b4b4b4;
}
.addcard__button {
  padding: 0;
  margin: 8px 0;
  width: 100%;
  font-size: 12px;
  line-height: 15px;
  font-weight: 600;
  height: 36px;
  border: none;
  background-color: rgba(123, 174, 115, 1);
  color: rgba(255, 255, 255, 1);
  border-radius: 10px;
}
.addcard__button:disabled {
  color: #b4b4b4;
  background-color: rgba(238, 238, 238, 1);
}

.addcard__button:hover {
  cursor: pointer;
}
.addcard__required {
  margin: 0 0 0 2px;
  display: block;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background-color: rgba(255, 132, 132, 1);
}
@media screen and (max-width: 744px) {
  .addcard {
    position: relative;
    max-width: 100%;
  }
}
</style>
