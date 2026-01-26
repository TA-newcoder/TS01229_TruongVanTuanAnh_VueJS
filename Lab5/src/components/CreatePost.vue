<script setup>
import { ref } from 'vue';

// Khai báo sự kiện để gửi dữ liệu ra ngoài
const emit = defineEmits(['add-post']);

const title = ref('');
const author = ref('');
const content = ref('');

const submitPost = () => {
  if (title.value && author.value && content.value) {
    const newPost = {
      title: title.value,
      author: author.value,
      content: content.value,
    };
    
    // Gửi dữ liệu ra component cha
    emit('add-post', newPost);

    // Reset form
    title.value = '';
    author.value = '';
    content.value = '';
  } else {
    alert("Vui lòng nhập đủ thông tin!");
  }
};
</script>

<template>
  <div class="card">
    <h2>Tạo bài viết mới</h2>
    <input v-model="title" placeholder="Tiêu đề bài viết" class="form-control" />
    <input v-model="author" placeholder="Tên tác giả" class="form-control" />
    <textarea v-model="content" placeholder="Nội dung bài viết" class="form-control"></textarea>
    <button @click="submitPost" class="btn-submit">Đăng bài</button>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ccc;
  padding: 20px;
  border-radius: 8px;
  background: white;
  margin-bottom: 30px; /* Tạo khoảng cách với danh sách bên dưới */
}

.form-control {
  display: block;
  width: 100%;
  margin-bottom: 15px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  box-sizing: border-box;
}

.btn-submit {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}
.btn-submit:hover {
  background-color: #2980b9;
}
</style>