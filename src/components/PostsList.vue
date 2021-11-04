<template>
  <div>
    <div class="row justify-content-center mb-5">
      <div class="col-sm-3">
        <NameFilter v-on:filter="getFilteredArr" />
      </div>
    </div>
    <ul class="row" style="gap: 30px 0">
      <li class="col-sm-4" v-for="post in setPostsList()" :key="post.id">
        <Post
          :title="post.title"
          :text="post.body"
          :author="getUsername(post.userId)"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Post from "./Post";
import NameFilter from "./NameFilter";

export default {
  name: "PostsList",
  components: { NameFilter, Post },
  data() {
    return {
      postsList: [],
      usersList: [],
      filteredPostsList: [],
    };
  },
  async created() {
    const postsList = await axios
      .get("http://jsonplaceholder.typicode.com/posts")
      .then((resp) => resp.data)
      .catch((err) => console.log(err));
    const usersList = await axios
      .get("http://jsonplaceholder.typicode.com/users")
      .then((resp) => resp.data)
      .catch((err) => console.log(err));
    this.postsList = postsList;
    this.usersList = usersList;
  },
  methods: {
    getUsername(userId) {
      const user = this.usersList.filter((el) => {
        return el.id === userId;
      });
      return user[0].username;
    },
    getPostByUser(userId) {
      return this.postsList.filter((el) => {
        return el.userId === userId;
      });
    },
    getFilteredArr(event) {
      let filteredUsers = this.usersList.filter((el) => {
        return el.username.toLowerCase().search(event.toLowerCase()) !== -1;
      });
      if (event !== "") {
        return (filteredUsers = filteredUsers.forEach((el) => {
          this.filteredPostsList = this.getPostByUser(el.id);
        }));
      }
      return (this.filteredPostsList = []);
    },
    setPostsList() {
      if (this.filteredPostsList.length > 0) {
        return this.filteredPostsList;
      }
      return this.postsList;
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
}
</style>
