<template>
  <div :class="[book.reminder ? 'reminder' : '', 'book']">
    <h3>
      {{ book.name }}
      <i @click="onDelete(book.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ book.auth }}</p>
  </div>
</template>

<script>
export default {
  name: "Book",
  props: {
    book: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-book", id);
    },
  },
};
</script>

<style scoped>
.fas {
  color: red;
}
.book {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.book.reminder {
  border-left: 5px solid green;
}

.book h3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
