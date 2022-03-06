<template>
  <div class="form">
    <form
      class="form__wrapper"
      action="#"
      @submit.prevent
      @submit="validateForm"
    >
      <label for="1">Наименование товара</label>
      <input
        id="1"
        v-model.trim="card.title"
        type="text"
        placeholder="Введите наименование товара"
      />
      <label for="2">Описание товара</label>
      <input
        id="2"
        v-model.trim="card.description"
        type="text"
        placeholder="Введите описание товара"
      />
      <label for="3">Ссылка на изображение товара</label>
      <input
        id="3"
        v-model.trim="card.image"
        type="text"
        placeholder="Введите ссылку"
      />
      <label for="4">Цена товара</label>
      <input
        id="4"
        v-model="card.price"
        type="number"
        placeholder="Введите цену"
      />
      <button @click="createPost" :disabled="isBtnDisabled">
        Добавить товар
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      card: {
        image: "",
        title: "",
        description: "",
        price: "",
      },
    };
  },

  computed: {
    isBtnDisabled() {
      return (
        this.card.image.length === 0 ||
        this.card.title.length === 0 ||
        this.card.description.length === 0 ||
        this.card.price.length === 0
      );
    },
  },

  methods: {
    createPost() {
      this.card.id = Date.now();
      this.$emit("add", this.card);
      this.card = {
        image: "",
        title: "",
        description: "",
        price: "",
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200;400;600&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200;400;600&display=swap");

.form {
  max-width: 332px;
  width: 100%;
  height: 440px;
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}

.form__wrapper {
  max-width: 284px;
  margin: 24px;
  display: flex;
  flex-direction: column;
}

.form label {
  font-family: "Source Sans Pro";
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  color: #49485e;
  position: relative;
  padding-bottom: 4px;
}

.form label:not(:nth-of-type(2))::after {
  content: url("../assets/image/dot.svg");
  margin-left: 1px;
  position: absolute;
  bottom: 9px;
}

.form label:first-of-type {
  margin: 0;
  padding-bottom: 4px;
}

.form input {
  background: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  min-height: 36px;
  padding-left: 16px;
}

.form input:hover {
  background: #e5e5e5;
}

.form input:not(:last-of-type) {
  margin-bottom: 16px;
}

.form input:nth-of-type(2) {
  min-height: 108px;
}

.form input:nth-of-type(2)::placeholder {
  position: absolute;
  top: 10px;
}

.form input::placeholder {
  font-family: "Source Sans Pro";
  font-size: 12px;
  line-height: 15px;
  color: #b4b4b4;
}

.form input:focus {
  background-color: #e6fff7;
}

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
}

.form button {
  font-family: "Inter";
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  letter-spacing: -0.02em;
  color: #b4b4b4;
  border: none;
  width: 100%;
  min-height: 36px;
  background: #eeeeee;
  border-radius: 10px;
  margin-top: 24px;
}

.form button:hover {
  opacity: 0.6;
  color: black;
  cursor: pointer;
}

.form button:active {
  background: black;
  color: white;
}
</style>
