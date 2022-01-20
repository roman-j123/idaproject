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
          v-bind:value="cardName"
          v-on:input="handleChangeInput"
          placeholder="Введите наименование товара"
        />
        <p v-if="errors.length" class="addcard__error">{{ errors[0] }}</p>
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
          v-bind:value="cardDescription"
          v-on:input="handleChangeInput"
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
          v-bind:value="cardImage"
          v-on:input="handleChangeInput"
          placeholder="Введите ссылку"
        />
        <p v-if="errors.length" class="addcard__error">{{ errors[1] }}</p>
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
          v-bind:value="cardPrice"
          v-on:input="handleChangeInput"
          placeholder="Введите цену"
        />
        <p v-if="errors.length" class="addcard__error">{{ errors[2] }}</p>
      </div>
      <button type="submit" class="addcard__button">Добавить товар</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      errors: [],
      cardName: "",
      cardDescription: "",
      cardImage: "",
      cardPrice: "",
    };
  },
  methods: {
    checkForm(event) {
      event.preventDefault();
      this.errors = [];
      if (!this.cardName) {
        this.errors.push("Укажите название карточки");
      }
      if (!this.cardImage) {
        this.errors.push("Необходимо указать ссылку на изображение");
      }
      if (!this.cardPrice) {
        this.errors.push("Необходимо указать стоимость товара");
      }
    },
    handleChangeInput(event) {
      console.log(event.target.form["card-name"].value);
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
  color: #b4b4b4;
  height: 36px;
  border: none;
  border-radius: 10px;
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
</style>
