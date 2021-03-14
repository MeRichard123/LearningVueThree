<template>
  <div>
    <form @submit.prevent="createPost">
      <div>
        <label for="userId">Post User Id</label>
        <input type="text" id="userId" v-model="formData.userId" />
      </div>
      <div>
        <label for="title">Post Title:</label>
        <input type="text" id="title" v-model="formData.title" />
      </div>
      <div>
        <label for="body">Post Body</label>
        <input type="text" id="body" v-model="formData.body" />
      </div>
      <button type="submit">Create Post</button>
    </form>
  </div>
  <div v-if="newPost">
    <h3>{{ newPost.id }}. {{ newPost.title }}</h3>
    <p>{{ newPost.body }}</p>
    <hr />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CreatePost",
  data() {
    return {
      formData: {
        userId: "",
        title: "",
        body: "",
      },
      newPost: {},
    };
  },
  methods: {
    createPost() {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", this.formData)
        .then((res) => {
          console.log(res);
          this.newPost = res.data;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped></style>
