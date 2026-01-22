<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const username = ref('');
const email = ref('');
const password = ref('');
const router = useRouter();

const handleRegister = () => {
  // Lấy danh sách user cũ từ LocalStorage (nếu chưa có thì tạo mảng rỗng)
  const users = JSON.parse(localStorage.getItem('users')) || [];

  // 1. Kiểm tra xem email đã tồn tại chưa
  if (users.find(u => u.email === email.value)) {
    alert('Email này đã được sử dụng!');
    return;
  }

  // 2. Tạo user mới
  const newUser = {
    id: Date.now(),
    username: username.value,
    email: email.value,
    password: password.value
  };

  // 3. Lưu vào LocalStorage
  users.push(newUser);
  localStorage.setItem('users', JSON.stringify(users));

  alert('Đăng ký thành công! Vui lòng đăng nhập.');
  router.push('/login'); // Chuyển sang trang đăng nhập
};
</script>

<template>
  <div class="row justify-content-center mt-5">
    <div class="col-md-6">
      <div class="card shadow">
        <div class="card-header bg-success text-white">
          <h4 class="mb-0">Đăng Ký Tài Khoản</h4>
        </div>
        <div class="card-body">
          <form @submit.prevent="handleRegister">
            <div class="mb-3">
              <label class="form-label">Họ và tên</label>
              <input type="text" class="form-control" v-model="username" required>
            </div>
            <div class="mb-3">
              <label class="form-label">Email</label>
              <input type="email" class="form-control" v-model="email" required>
            </div>
            <div class="mb-3">
              <label class="form-label">Mật khẩu</label>
              <input type="password" class="form-control" v-model="password" required>
            </div>
            <button type="submit" class="btn btn-success w-100">Đăng ký ngay</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>