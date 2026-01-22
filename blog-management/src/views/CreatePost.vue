<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const title = ref('');
const content = ref('');
const router = useRouter();

const handlePost = () => {
  // 1. Lấy thông tin người đang đăng nhập
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  
  if (!currentUser) {
    alert('Bạn phải đăng nhập mới được đăng bài!');
    router.push('/login');
    return;
  }

  // 2. Lấy danh sách bài viết cũ
  const posts = JSON.parse(localStorage.getItem('posts')) || [];

  // 3. Tạo bài viết mới
  const newPost = {
    id: Date.now(),
    title: title.value,
    content: content.value,
    author: currentUser.username, // Lưu tên người viết
    date: new Date().toLocaleDateString()
  };

  // 4. Lưu lại
  posts.unshift(newPost); // Thêm vào đầu danh sách
  localStorage.setItem('posts', JSON.stringify(posts));

  alert('Đăng bài thành công!');
  router.push('/'); // Quay về trang chủ
};
</script>

<template>
  <div class="card shadow mt-4">
    <div class="card-header bg-info text-white">
      <h4>Viết bài mới</h4>
    </div>
    <div class="card-body">
      <form @submit.prevent="handlePost">
        <div class="mb-3">
          <label class="form-label font-weight-bold">Tiêu đề bài viết</label>
          <input type="text" class="form-control" v-model="title" required placeholder="Ví dụ: Review VueJS...">
        </div>
        <div class="mb-3">
          <label class="form-label font-weight-bold">Nội dung</label>
          <textarea class="form-control" rows="5" v-model="content" required placeholder="Nhập nội dung ở đây..."></textarea>
        </div>
        <button type="submit" class="btn btn-info text-white">Đăng bài ngay</button>
      </form>
    </div>
  </div>
</template>