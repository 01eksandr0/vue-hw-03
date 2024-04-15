<template>
  <div class="app">
    <contacts-form @submit="createUser" />
    <search-box :updateSearchQuery="updateSearchQuery"></search-box>
    <div class="list" v-if="contacts.length">
      <contact-item
        v-for="contact in filterList"
        :contact="contact"
        :key="contact.id"
        @click="deleteItem"
      />
    </div>
    <p v-else>You dont have contacts</p>
  </div>
</template>

<script>
import ContactsForm from "./components/ContactsForm.vue";
import SearchBox from "./components/SearchBox.vue";
import ContactItem from "./components/ContactItem.vue";
export default {
  components: { ContactsForm, SearchBox, ContactItem },
  data() {
    return {
      searchQuery: "",
      contacts: [],
    };
  },
  methods: {
    updateSearchQuery(newQuery) {
      this.searchQuery = newQuery;
    },
    createUser({ name, number }) {
      if (name && number) this.contacts.push({ name, number, id: Date.now() });
    },
    deleteItem(id) {
      this.contacts = this.contacts.filter((i) => i.id !== id);
    },
  },
  watch: {
    contacts: {
      handler() {
        localStorage.setItem("key", JSON.stringify(this.contacts));
      },
      deep: true,
    },
  },
  computed: {
    filterList() {
      return this.contacts.filter(
        (i) =>
          i.name.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
          i.number.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  created() {
    const data = localStorage.getItem("key");
    this.contacts = JSON.parse(data) || [];
  },
};
</script>

<style scoped>
.app {
  padding: 40px;
}
.list {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
</style>
