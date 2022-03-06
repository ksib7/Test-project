<template>
  <div>
    <div class="select" @click="isOptionsVisible = !isOptionsVisible">
      <p class="select__title">По умолчанию</p>
      <div class="select__options" v-if="isOptionsVisible">
        <p
          v-for="option in options"
          :key="option.value"
          @click="changeOption(option)"
        >
          {{ option.name }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOptionsVisible: false,
    };
  },

  props: {
    options: {
      type: Array,
      default() {
        return [];
      },
    },
  },

  methods: {
    changeOption(option) {
      this.$emit("change", option);
      this.isOptionsVisible = !isOptionsVisible;
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200;400;600&display=swap");

.select {
  font-family: "Source Sans Pro";
  width: 121px;
  height: 36px;
  font-size: 12px;
  line-height: 15px;
  color: #b4b4b4;
  background: #fffefb;
  box-shadow: 0px 2px 5px rgb(0 0 0 / 10%);
  border-radius: 4px;
  text-align: center;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.select__title {
  justify-content: center;
}

.select__title::after {
  content: url("../assets/image/arrow-down.svg");
  padding-left: 5px;
}

.select__options {
  position: absolute;
  top: 40px;
  z-index: 1;
  width: 100%;
  color: #b4b4b4;
  background: #fffefb;
  box-shadow: 0px 2px 5px rgb(0 0 0 / 10%);
  border-radius: 4px;
}

.select__options p {
  padding: 10px 0;
}

.select__options p:hover {
  background: #e7e7e7;
  cursor: pointer;
}

.select__options p:last-of-type:hover {
  border-bottom-left-radius: 4px;
  border-bottom-right-radius: 4px;
}

.select__options p:first-of-type:hover {
  border-top-left-radius: 4px;
  border-top-right-radius: 4px;
}

.select:hover {
  cursor: pointer;
}
</style>
