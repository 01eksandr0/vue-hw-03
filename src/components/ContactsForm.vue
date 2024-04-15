<template>
  <form class="form" @submit.prevent="createUser">
    <label class="label">
      Name
      <my-input type="text" placeholder="Name" v-model="name"
    /></label>
    <label class="label">
      Number
      <my-input type="text" placeholder="Number" v-model="number"
    /></label>
    <my-button>Create Contact</my-button>
  </form>
</template>

<script>
import MyButton from "./UI/MyButton.vue";
import MyInput from "./UI/MyInput.vue";
export default {
  name: "contacts-form",
  components: { MyInput, MyButton },
  data() {
    return {
      name: "",
      number: "",
    };
  },
  methods: {
    createUser() {
      this.$emit("submit", { name: this.name, number: this.number });
      this.name = "";
      this.number = "";
    },
  },
};
</script>

<style lang="css" scoped>
.form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 20px;
  padding: 20px 40px;
  border-radius: 10px;
  border: 1px solid #000;
  width: 300px;
}

.label {
  display: flex;
  flex-direction: column;
  gap: 6px;
  align-items: start;
  width: 100%;
}
</style>
