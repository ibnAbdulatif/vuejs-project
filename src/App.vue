<template>
  <div class="container">
    <Header
      @toggle-add-book="toggleAddBook"
      title="Add Book"
      :showAddBook="showAddBook"
    />
    <div v-if="showAddBook">
      <AddBook @add-book="addBook" />
    </div>
    <Books
      @toggle-reminder="toggleReminder"
      @delete-book="deleteBook"
      :books="books"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Books from "./components/Books";
import AddBook from "./components/AddBook";
export default {
  name: "App",
  components: {
    Header,
    Books,
    AddBook,
  },
  data() {
    return {
      books: [],
      showAddBook: false,
    };
  },
  methods: {
    toggleAddBook() {
      this.showAddBook = !this.showAddBook;
    },
    addBook(book) {
      this.books = [...this.books, book];
    },
    deleteBook(id) {
      if (confirm("Are you delete this Book")) {
        this.books = this.books.filter((book) => book.id !== id);
      }
    },
    toggleReminder(id) {
      this.books = this.books.map((book) =>
        book.id === id ? { ...book, reminder: !book.reminder } : book
      );
    },
  },
  created() {
    this.books = [
      {
        id: 1,
        name: "O`tgan kunlar",
        auth: "Abdulla Qodiriy",
        reminder: true,
      },
      {
        id: 2,
        name: "Bolalik",
        auth: "Oybek",
        reminder: true,
      },
      {
        id: 3,
        name: "Don Kixot",
        auth: "Servantes",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,600;0,700;1,400;1,500&display=swap");
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
