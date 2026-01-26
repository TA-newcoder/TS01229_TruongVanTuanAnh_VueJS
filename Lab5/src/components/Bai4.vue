<script setup>
import { ref } from 'vue';
import CreatePost from './CreatePost.vue';
import PostList from './PostList.vue';

const posts = ref([]);

const addPost = (newPost) => {
  // Random màu nền (Style binding yêu cầu đề bài)
  const colors = ['#fff', '#e3f2fd', '#fbe9e7', '#f1f8e9'];
  const randomColor = colors[Math.floor(Math.random() * colors.length)];

  posts.value.push({
    ...newPost,
    bgColor: randomColor
  });
};
</script>

<template>
  <div class="lab4-layout">
    <h1 class="main-title">Bài 4: Blog Ứng Dụng</h1>
    
    <CreatePost @add-post="addPost" />

    <PostList :posts="posts" />
  </div>
</template>

<style scoped>
.lab4-layout {
  max-width: 800px;
  margin: 0 auto; /* Căn giữa màn hình */
  padding: 20px;
  font-family: 'Segoe UI', sans-serif;
}

.main-title {
  text-align: center;
  color: #333;
  margin-bottom: 30px;
}
</style>