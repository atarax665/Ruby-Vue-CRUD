<template>
  <div class="bg-white shadow-md rounded-lg p-4 mb-4">
    <!-- Post card to show title, post and Id -->
    <div class="post-card">
      <h2 class="text-xl font-semibold mb-2">{{ title }}</h2>
      <p class="text-gray-700 mb-2">{{ post }}</p>
      <p class="text-gray-500 text-sm">{{ id }}</p>
    </div>

    <!-- Add edit button that will open their content in input box of post component -->
    <div class="mt-4 flex space-x-2">
      <button
        @click="editPost"
        class="bg-blue-500 text-white px-4 py-2 rounded"
      >
        Edit
      </button>
      <button
        @click="deletePost"
        class="bg-red-500 text-white px-4 py-2 rounded"
      >
        Delete
      </button>
    </div>
  </div>
</template>
<script>
  export default {
    name: "PostCard",
    props: {
      title: String,
      post: String,
      id: Number,
    },
    data() {
      return {};
    },
    methods: {
      editPost() {
        this.$emit("edit-post", {
          title: this.title,
          post: this.post,
          id: this.id,
        });
      },
      deletePost() {
        this.$emit("delete-post", this.id);
      },
    },
  };
</script>

<style scoped></style>
