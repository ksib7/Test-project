<template>
  <div>
    <select class="select" v-model="modelValue" @change="changeOption">
      <option disabled value="">По умолчанию</option>
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
      >
        {{ option.name }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => [],
    },
  },

  methods: {
    changeOption(event) {
      this.$emit("update: modelValue", event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.select {
  border: none;
  font-size: 12px;
  line-height: 15px;
  color: #b4b4b4;
  background: #fffefb;
  box-shadow: 0px 2px 5px rgb(0 0 0 / 10%);
  border-radius: 4px;
  height: 32px;
  align-self: center;
  text-align: center;
}

.select:hover {
  opacity: 0.6;
  color: black;
  cursor: pointer;
}

.select:active {
  background: black;
  color: white;
}
</style>
