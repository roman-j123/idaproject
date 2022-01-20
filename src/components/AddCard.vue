<template>
  <div class="addcard">
    <form action="POST" class="addcard__form">
      <label for="card-name" class="addcard__title">Наименование товара</label>
      <span class="addcard__required"></span>
      <input
        class="addcard__input"
        type="text"
        id="card-name"
        placeholder="Введите наименование товара"
        required
      />
      <label for="card-description" class="addcard__title"
        >Описание товара</label
      >
      <textarea
        class="addcard__input addcard__input_description"
        type="text"
        maxlength="200"
        id="card-description"
        placeholder="Введите описание товара"
      ></textarea>
      <label for="card-href" class="addcard__title"
        >Ссылка на изображение товара</label
      >
      <span class="addcard__required"></span>
      <input
        class="addcard__input"
        type="url"
        id="card-href"
        placeholder="Введите ссылку"
        required
      />
      <label for="card-price" class="addcard__title">Цена товара</label>
      <span class="addcard__required"></span>
      <input
        class="addcard__input"
        type="number"
        id="card-price"
        placeholder="Введите цену"
        required
      />
      <button type="submit" class="addcard__button">Добавить товар</button>
    </form>
  </div>
</template>
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
  flex-wrap: wrap;
}
.addcard__title {
  margin: 0 0 4px 0;
  font-size: 10px;
  font-weight: 400;
  line-height: 12px;
}
.addcard__input {
  margin: 0 0 16px 0;
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