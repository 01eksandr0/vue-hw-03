<template>
  <div class="item">
    <div class="container">
      <p class="text">{{ contact.name }}</p>
      <p class="text">{{ contact.number }}</p>
    </div>
    <my-button type="button" @click="$emit('click', contact.id)"
      >Delete</my-button
    >
  </div>
</template>

<script>
import MyButton from "./UI/MyButton.vue";
export default {
  name: "contact-item",
  components: { MyButton },
  props: {
    contact: Object,
  },
};
</script>

<style lang="css" scoped>
.item {
  height: 80px;
  width: 240px;
  border: 1px solid #000;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
}
.container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
