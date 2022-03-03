<template>
  <div>
    <div class="header">
      <h1>Добавление товара</h1>
      <itemSelect v-model="selectedSort" :options="sortOptions" />
    </div>
    <div class="items">
      <itemForm @add="addItem"></itemForm>
      <itemList @remove="removeItem" :cards="sortedItems"></itemList>
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

  computed: {
    sortedItems() {
      return [...this.cards].sort((item1, item2) =>
        item1[this.selectedSort]?.localCompare(item2[this.selectedSort])
      );
    },
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
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
  color: #3f3f3f;
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
