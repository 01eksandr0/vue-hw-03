<template>
  <input class="input" :value="modelValue" @input="updateInput" />
</template>

<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>

<style lang="css" scoped>
.input {
  height: 40px;
  width: 100%;
  border-radius: 10px;
  outline: none;
  padding-left: 10px;
}
</style>
