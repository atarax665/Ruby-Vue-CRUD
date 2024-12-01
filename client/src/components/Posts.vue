<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div class="container mx-auto p-4 bg-white shadow-md rounded-lg">
      <h1 class="text-3xl font-bold underline mb-4 text-center">Posts</h1>
      <div class="mb-4">
        <input
          type="text"
          placeholder="Title"
          v-model="title"
          class="title-input border rounded p-2 w-full mb-2"
        />
        <input
          type="text"
          placeholder="Post"
          v-model="body"
          class="post-input border rounded p-2 w-full mb-2"
        />
      </div>
      <div class="mb-4 text-center">
        <button
          v-if="isEditing"
          @click="updatePost"
          class="bg-blue-500 text-white px-4 py-2 rounded mr-2"
        >
          Update Post
        </button>
        <button
          v-if="isEditing"
          @click="cancelEditing"
          class="bg-gray-500 text-white px-4 py-2 rounded mr-2"
        >
          Cancel
        </button>
        <button
          v-else
          @click="addPost"
          class="bg-blue-500 text-white px-4 py-2 rounded"
        >
          Add Post
        </button>
      </div>
      <div>
        <PostCard
          v-for="(post, index) in postData"
          :key="index"
          :title="post.title"
          :post="post.body"
          :id="post.id"
          @edit-post="editPost"
          @delete-post="removePost"
          class="mb-4"
        />
      </div>
    </div>
  </div>
</template>

<script>
  import { ref } from "vue";
  import PostCard from "./PostCard.vue";
  import {
    getPosts,
    createPost,
    updatePost,
    deletePost,
  } from "../shared/services/post_service";

  export default {
    name: "Posts",
    components: {
      PostCard,
    },
    data() {
      return {
        title: "",
        body: "",
        id: 0,
        postId: 0,
        isEditing: false,
        postData: [],
      };
    },
    async mounted() {
      const res = await getPosts();
      this.postData = res;
    },
    methods: {
      async addPost() {
        const res = await createPost({
          title: this.title,
          body: this.body,
        });

        this.postData.push(res);
        this.title = "";
        this.body = "";
        id = 0;
      },
      async updatePost() {
        const res = await updatePost({
          id: this.postId,
          title: this.title,
          body: this.body,
        });

        const index = this.postData.findIndex(
          (post) => post.id === this.postId
        );
        this.postData[index] = res;

        this.title = "";
        this.body = "";
        this.postId = 0;
        this.isEditing = false;
      },
      cancelEditing() {
        this.title = "";
        this.body = "";
        this.postId = 0;
        this.isEditing = false;
      },
      editPost(post) {
        const { title, post: body, id } = post;
        const editable = this.postData.find((post) => post.id === id);
        this.title = editable.title;
        this.body = editable.body;
        this.postId = id;
        this.isEditing = true;

        window.scrollTo({
          top: 0,
          behavior: "smooth",
        });
      },
      async removePost(id) {
        deletePost(id);

        this.postData = this.postData.filter((post) => post.id !== id);
      },
    },
  };
</script>

<style scoped></style>
