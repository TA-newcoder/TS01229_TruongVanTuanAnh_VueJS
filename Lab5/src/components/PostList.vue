<script setup>
// Nhận dữ liệu từ cha truyền xuống
defineProps({
  posts: Array
});
</script>

<template>
  <div class="list-container">
    <h2>Danh sách bài viết</h2>

    <p v-if="posts.length === 0" style="color: gray">Chưa có bài viết nào.</p>

    <div 
      v-for="(post, index) in posts" 
      :key="index"
      class="post-item"
      :class="{ 'highlight': post.title.length > 20 }"
      :style="{ backgroundColor: post.bgColor }"
    >
      <h3 class="text-success">{{ post.title }}</h3>
      <h4 class="text-danger">{{ post.author }}</h4>
      <p>{{ post.content }}</p>
    </div>
  </div>
</template>

<style scoped>
.post-item {
  padding: 20px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

/* Class Binding: Viền đỏ nếu tiêu đề dài */
.highlight {
  border: 2px solid #e74c3c;
}

.text-success { color: #2ecc71; margin-bottom: 5px; }
.text-danger { color: #e74c3c; margin-top: 0; font-style: italic; }
</style>