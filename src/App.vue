<template>
  <div class="container">
    <preloader-page />
    <router-view :cards="cards" />
  </div>
</template>

<script>
import preloaderPage from "./components/preloaderPage.vue";
export default {
  components: {
    preloaderPage,
  },

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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: rgba(255, 254, 251, 0.8);
}

.container {
  max-width: 1440px;
  width: 100%;
  margin: 0 auto;
  padding: 32px;
}
</style>
