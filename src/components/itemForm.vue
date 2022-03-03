<template>
  <div class="form">
    <form action="#" @submit.prevent @submit="validateForm">
      <h2>Наименование товара</h2>
      <input
        v-model.trim="card.title"
        type="text"
        placeholder="Введите наименование товара"
      />
      <h2>Описание товара</h2>
      <input
        v-model.trim="card.description"
        type="text"
        placeholder="Введите описание товара"
      />
      <h2>Ссылка на изображение товара</h2>
      <input
        v-model.trim="card.image"
        type="text"
        placeholder="Введите ссылку"
      />
      <h2>Цена товара</h2>
      <input v-model.trim="card.price" type="text" placeholder="Введите цену" />
      <button @click="createPost">Добавить товар</button>
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
.form {
  max-width: 332px;
  width: 100%;
  height: 440px;
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}

.form h2 {
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  color: #49485e;
  margin-left: 24px;
  position: relative;
  margin-bottom: 4px;
}

.form h2:not(:nth-of-type(2))::after {
  content: url("../assets/image/dot.svg");
  margin-left: 1px;
  position: absolute;
  bottom: 6px;
}

.form h2:not(:first-of-type) {
  margin-top: 16px;
}

.form h2:first-of-type {
  padding-top: 24px;
  margin: 0;
  margin-left: 24px;
  margin-bottom: 4px;
}

.form input {
  width: 88%;
  background: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  min-height: 36px;
  margin-left: 24px;
  padding-left: 16px;
}

.form input:nth-of-type(2) {
  min-height: 108px;
}

.form input:nth-of-type(2)::placeholder {
  position: absolute;
  top: 10px;
}

.form input::placeholder {
  font-size: 12px;
  line-height: 15px;
  color: #b4b4b4;
}

.form input:focus {
  background-color: #e6fff7;
}

.form button {
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  letter-spacing: -0.02em;
  color: #b4b4b4;
  border: none;
  width: 88%;
  min-height: 36px;
  background: #eeeeee;
  border-radius: 10px;
  margin-top: 24px;
  margin-left: 24px;
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
