<template>
  <div class="wrapper">
    <transition-group name="list">
      <div v-if="show" class="cards">
        <transition-group name="cards">
          <div class="cards__items" v-for="item in cards" :key="item.id">
            <img :src="item.image" alt="image" class="cards__items__pic" />
            <h2>{{ item.title }}</h2>
            <p>{{ item.description }}</p>
            <div>{{ item.price }}<span> руб.</span></div>
            <button @click="remove(item.id)" class="cards__items__btn">
              <img src="img/delete.svg" alt="deleteButton" />
            </button>
          </div>
        </transition-group>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: ["cards"],

  data() {
    return {
      show: false,
    };
  },

  mounted() {
    this.showCards();
  },

  methods: {
    remove(id) {
      this.$emit("remove", id);
    },

    showCards() {
      setTimeout(() => {
        this.show = true;
      }, 700);
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200;400;600&display=swap");
.wrapper {
  width: 100%;
}

.cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  width: 100%;
  gap: 16px;
}

.cards__items__pic {
  width: 100%;
  min-height: 200px;
  border: 4 4 0 0;
}

.cards__items {
  width: 100%;
  min-height: 423px;
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  position: relative;
}

.cards__items h2 {
  font-family: "Source Sans Pro";
  font-weight: 600;
  font-size: 20px;
  line-height: 25px;
  color: #3f3f3f;
  padding-top: 16px;
  padding-left: 16px;
}

.cards__items p {
  font-family: "Source Sans Pro";
  font-size: 16px;
  line-height: 20px;
  color: #3f3f3f;
  padding-top: 16px;
  padding-left: 16px;
}

.cards__items div {
  font-family: "Source Sans Pro";
  font-weight: 600;
  font-size: 24px;
  line-height: 30px;
  color: #3f3f3f;
  padding-top: 32px;
  padding-left: 16px;
}

.cards__items__btn {
  height: 32px;
  background: #ff8484;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  border: none;
  position: absolute;
  top: -8px;
  right: -8px;
  opacity: 0;
}

.cards__items__btn img {
  padding: 8px;
}

.cards__items:hover .cards__items__btn {
  opacity: 1;
  cursor: pointer;
}

.cards__items:active .cards__items__btn {
  opacity: 0.6;
}

.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.cards-item {
  display: inline-block;
  margin-right: 10px;
}
.cards-enter-active,
.cards-leave-active {
  transition: all 0.5s ease;
}
.cards-enter-from,
.cards-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

@media (max-width: 1200px) {
  .cards {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 906px) {
  .cards {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 549px) {
  .cards {
    margin-top: 70px;
  }
}
</style>
