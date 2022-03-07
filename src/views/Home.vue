<template>
  <div>
    <div class="header">
      <h1>Добавление товара</h1>
      <itemSelect v-model="selectedSort" :options="sortOptions" />
    </div>
    <div class="items">
      <itemForm @add="addItem" @submit="validateForm"></itemForm>
      <itemList @remove="removeItem" :cards="cards"></itemList>
    </div>
  </div>
</template>

<script>
import itemForm from "../components/itemForm.vue";
import itemList from "../components/itemList.vue";
import itemSelect from "../components/itemSelect.vue";

export default {
  props: ["cards"],

  data() {
    return {
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "По наименованию" },
        { value: "min", name: "По цене min" },
        { value: "max", name: "По цене max" },
      ],
    };
  },

  components: {
    itemForm,
    itemList,
    itemSelect,
  },

  methods: {
    addItem(card) {
      this.cards.push(card);
      window.localStorage.setItem("cards-products", JSON.stringify(this.cards));
    },

    removeItem(id) {
      const indx = this.cards.findIndex((item) => item.id == id);
      this.cards.splice(indx, 1);
      window.localStorage.setItem("cards-products", JSON.stringify(this.cards));
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200;400;600&display=swap");

.items {
  display: flex;
  justify-content: space-between;
  gap: 16px;
}

.header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 16px;
}

.header h1 {
  font-family: "Source Sans Pro";
  font-style: normal;
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
  color: #3f3f3f;
}

.header button {
  max-width: 121px;
  width: 100%;
  min-height: 32px;
  border: none;
  font-size: 12px;
  line-height: 15px;
  color: #b4b4b4;
  background: #fffefb;
  box-shadow: 0px 2px 5px rgb(0 0 0 / 10%);
  border-radius: 4px;
  align-self: center;
  text-align: center;
}

.header button::after {
  content: url("../assets/image/arrow-down.svg");
  padding-left: 5px;
}

.header button:hover {
  opacity: 0.6;
  color: black;
  cursor: pointer;
}

.header button:active {
  background: black;
  color: white;
}

@media (max-width: 549px) {
  .items {
    flex-direction: column;
    align-items: center;
  }

  .header h1 {
    font-size: 20px;
  }
}
</style>
