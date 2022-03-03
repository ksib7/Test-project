<template>
  <div class="container">
    <router-view :cards="cards" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: [],
    };
  },

  mounted() {
    this.cards = [
      {
        id: 0,
        image: "/img/card.jpg",
        title: "Наименование товара",
        description:
          "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        price: "10 000 руб.",
      },
      {
        id: 1,
        image: "/img/card.jpg",
        title: "Наименование товара",
        description:
          "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        price: "10 000 руб.",
      },
      {
        id: 2,
        image: "/img/card.jpg",
        title: "Наименование товара",
        description:
          "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        price: "10 000 руб.",
      },
      {
        id: 3,
        image: "/img/card.jpg",
        title: "Наименование товара",
        description:
          "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        price: "10 000 руб.",
      },
      {
        id: 4,
        image: "/img/card.jpg",
        title: "Наименование товара",
        description:
          "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        price: "10 000 руб.",
      },
      {
        id: 5,
        image: "/img/card.jpg",
        title: "Наименование товара",
        description:
          "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        price: "10 000 руб.",
      },
    ];

    this.cards =
      JSON.parse(window.localStorage.getItem("cards-products")) || [];
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1440px;
  width: 100%;
  margin: 0 auto;
  padding: 32px 10px;
}

body {
  background: #e5e5e5;
  font-family: "Source Sans Pro", sans-serif;
}
</style>
