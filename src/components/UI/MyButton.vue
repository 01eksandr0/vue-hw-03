<template>
  <button class="btn" :type="type" @click="$emit('click')">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "my-button",
  props: {
    type: {
      type: String,
      default: "submit",
    },
  },
};
</script>

<style lang="css" scoped>
.btn {
  padding: 8px 12px;
  background-color: #767676;
  border-radius: 10px;
  border: none;
  color: #fff;
}
</style>
