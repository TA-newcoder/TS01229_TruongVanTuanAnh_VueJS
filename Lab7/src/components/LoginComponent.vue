<script setup>
import { ref } from 'vue';

// 1. Khai báo sự kiện 'loggedIn' để bắn ra ngoài cho cha biết
const emit = defineEmits(['loggedIn']);

const username = ref('');
const password = ref('');

// 2. Hàm xử lý đăng nhập
const handleLogin = () => {
  if (username.value && password.value) {
    // Bắn sự kiện 'loggedIn' kèm theo dữ liệu là username
    emit('loggedIn', username.value);
  } else {
    alert("Vui lòng nhập đầy đủ thông tin!");
  }
}
</script>

<template>
  <div class="p-5 border rounded shadow-sm bg-white" style="max-width: 400px; margin: 0 auto;">
    <h3 class="text-center fw-bold mb-4">Đăng Nhập</h3>
    
    <form @submit.prevent="handleLogin">
      <div class="mb-3">
        <label class="form-label fw-bold">Tên đăng nhập:</label>
        <input 
          type="text" 
          class="form-control" 
          v-model="username" 
          placeholder="Nhập tên..."
        >
      </div>

      <div class="mb-3">
        <label class="form-label fw-bold">Mật khẩu:</label>
        <input 
          type="password" 
          class="form-control" 
          v-model="password" 
          placeholder="Nhập mật khẩu..."
        >
      </div>

      <button type="submit" class="btn btn-primary w-100">
        Đăng nhập
      </button>
    </form>
  </div>
</template>