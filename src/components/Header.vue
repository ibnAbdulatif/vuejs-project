<template>
  <header>
    <h1>Hello World</h1>
    <Button text="Add text" color="green" />
  </header>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  components: {
    Button,
  },
};
</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
