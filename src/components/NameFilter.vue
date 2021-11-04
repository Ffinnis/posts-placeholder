<template>
  <b-form-input
    @input="$emit('filter', $event)"
    v-model="author"
    placeholder="Steve"
  />
</template>

<script>
export default {
  name: "NameFilter",
  data() {
    return {
      author: "",
    };
  },
};
</script>

<style scoped></style>
