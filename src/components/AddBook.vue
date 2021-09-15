<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="name">Book Name</label>
      <input type="text" v-model="name" name="name" placeholder="Add Book" />
    </div>
    <div class="form-control">
      <label for="auth">Author</label>
      <input type="text" v-model="auth" name="auth" placeholder="Add Author" />
    </div>
    <div class="form-control form-control-check">
      <label for="">Checked</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <input type="submit" value="save book" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddBook",
  data() {
    return {
      name: "",
      auth: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.name || !this.auth) {
        alert("Pleese add book");
        return;
      }

      const newBook = {
        id: Math.floor(Math.random() * 1000000),
        name: this.name,
        auth: this.auth,
        reminder: this.reminder,
      };

      this.$emit("add-book", newBook);
      this.name = "";
      this.auth = "";
      this.reminder = false;
    },
  },
};
</script>
\

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0px;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}
</style>
