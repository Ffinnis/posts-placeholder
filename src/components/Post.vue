<template>
  <b-card :header="title" align="left" header-text-variant="primary">
    <b-card-text>
      {{ text }}
    </b-card-text>
    <p class="author mt-4">{{ author }}</p>
  </b-card>
</template>

<script>
export default {
  props: {
    title: String,
    text: String,
    author: String,
  },
  name: "Post",
};
</script>

<style lang="scss" scoped>
.author {
  font-size: 24px;
  font-weight: 600;
  color: #948e8e;
}
</style>
