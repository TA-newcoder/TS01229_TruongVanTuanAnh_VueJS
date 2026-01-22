<script setup>
import { ref, onMounted } from 'vue';

const posts = ref([]);
const currentUser = ref(null);

onMounted(() => {
  // 1. Lấy danh sách bài viết
  posts.value = JSON.parse(localStorage.getItem('posts')) || [];
  
  // 2. Lấy thông tin người đang đăng nhập (để kiểm tra quyền xóa)
  currentUser.value = JSON.parse(localStorage.getItem('currentUser'));
});

// Hàm xử lý Xóa bài viết
const deletePost = (id) => {
  // Hỏi xác nhận trước khi xóa
  if (confirm('Bạn có chắc chắn muốn xóa bài viết này không?')) {
    // Lọc bỏ bài viết có id tương ứng
    posts.value = posts.value.filter(post => post.id !== id);
    
    // Lưu danh sách mới lại vào LocalStorage
    localStorage.setItem('posts', JSON.stringify(posts.value));
  }
};
</script>

<template>
  <div class="home mt-4">
    <div class="d-flex justify-content-between align-items-center mb-4">
      <h1>Danh sách bài viết</h1>
      <router-link to="/create-post" class="btn btn-primary">
        + Viết bài mới
      </router-link>
    </div>

    <div v-if="posts.length === 0" class="alert alert-warning">
      Chưa có bài viết nào. Hãy là người đầu tiên đăng bài!
    </div>

    <div class="row">
      <div class="col-md-12 mb-3" v-for="post in posts" :key="post.id">
        <div class="card shadow-sm">
          <div class="card-body">
            <div class="d-flex justify-content-between">
              <h3 class="card-title text-primary">{{ post.title }}</h3>
              
              <button 
                v-if="currentUser && currentUser.username === post.author" 
                @click="deletePost(post.id)" 
                class="btn btn-outline-danger btn-sm"
              >
                Xóa bài
              </button>
            </div>

            <h6 class="card-subtitle mb-2 text-muted">
              Đăng bởi: <strong>{{ post.author }}</strong> - Ngày: {{ post.date }}
            </h6>
            <p class="card-text mt-3">{{ post.content }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>