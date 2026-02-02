<script setup>
import { ref } from 'vue';

// 1. Các biến trạng thái
const isLoggedIn = ref(false);
const email = ref('');
const password = ref('');

// Biến lưu thông báo lỗi
const emailError = ref('');
const passwordError = ref('');

// Regex kiểm tra định dạng email
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

// 2. Hàm xử lý Đăng nhập
const login = () => {
  // Reset lỗi mỗi lần bấm nút
  emailError.value = '';
  passwordError.value = '';

  // Validate Email
  if (!email.value) {
    emailError.value = 'Email là bắt buộc.';
  } else if (!emailRegex.test(email.value)) {
    emailError.value = 'Vui lòng nhập email hợp lệ.';
  }

  // Validate Mật khẩu
  if (!password.value) {
    passwordError.value = 'Mật khẩu là bắt buộc.';
  }

  // Nếu không có lỗi nào thì cho đăng nhập thành công
  if (!emailError.value && !passwordError.value) {
    isLoggedIn.value = true;
  }
}

// 3. Hàm xử lý Đăng xuất
const logout = () => {
  isLoggedIn.value = false;
  email.value = '';
  password.value = '';
  emailError.value = '';
  passwordError.value = '';
}
</script>

<template>
  <div class="d-flex justify-content-center mt-5">
    
    <div v-if="!isLoggedIn" class="card p-4 shadow-sm" style="width: 400px;">
      <h3 class="fw-bold mb-3">Form Đăng nhập</h3>
      
      <form @submit.prevent="login">
        <div class="mb-3">
          <label class="form-label fw-bold">Email:</label>
          <input 
            type="text" 
            class="form-control" 
            v-model="email" 
            placeholder="Nhập email"
            :class="{ 'is-invalid': emailError }" 
          >
          <div v-if="emailError" class="text-danger mt-1 small">
            {{ emailError }}
          </div>
        </div>

        <div class="mb-3">
          <label class="form-label fw-bold">Mật khẩu:</label>
          <input 
            type="password" 
            class="form-control" 
            v-model="password" 
            placeholder="Nhập mật khẩu"
            :class="{ 'is-invalid': passwordError }"
          >
          <div v-if="passwordError" class="text-danger mt-1 small">
            {{ passwordError }}
          </div>
        </div>

        <button type="submit" class="btn btn-primary">
          Đăng nhập
        </button>
      </form>
    </div>

    <div v-else class="card p-4 shadow-sm" style="width: 400px;">
      <h3 class="fw-bold mb-3">Chào mừng, {{ email }}!</h3>
      
      <button @click="logout" class="btn btn-primary" style="width: fit-content;">
        Đăng xuất
      </button>
    </div>

  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ccc;
  border-radius: 5px;
}
.small {
  font-size: 0.875rem;
}
</style>