<template>
  <div class="custom-checkbox" @click="toggleCheck">
    <div v-if="value === 0"></div>
    <div v-else-if="value === 1">&bull;</div>
    <div v-else>&#10004;</div>
  </div>
</template>

<script>
export default {
  props: {
    value: Number,
  },
  data() {
    return {};
  },
  methods: {
    toggleCheck() {
      this.$emit("input", this.value);
    },
  },
};
</script>

<style scoped>
.custom-checkbox {
  cursor: pointer;
  user-select: none;
  display: inline-block;
  width: 20px;
  height: 20px;
  text-align: center;
  border: 1px solid #000;
}
</style>
