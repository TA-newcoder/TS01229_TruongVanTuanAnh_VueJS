<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const email = ref('');
const password = ref('');
const router = useRouter();

const handleLogin = () => {
  const users = JSON.parse(localStorage.getItem('users')) || [];
  
  // Tìm người dùng khớp thông tin
  const user = users.find(u => u.email === email.value && u.password === password.value);

  if (user) {
    // Lưu session đăng nhập
    localStorage.setItem('currentUser', JSON.stringify(user));
    alert('Đăng nhập thành công!');
    
    // Chuyển về trang chủ và reload để cập nhật Navbar
    router.push('/');
    setTimeout(() => { window.location.reload(); }, 100);
  } else {
    alert('Sai thông tin đăng nhập!');
  }
};
</script>

<template>
  <div class="row justify-content-center mt-5">
    <div class="col-md-6">
      <div class="card shadow">
        <div class="card-header bg-primary text-white">
          <h4 class="mb-0">Đăng Nhập</h4>
        </div>
        <div class="card-body">
          <form @submit.prevent="handleLogin">
            <div class="mb-3">
              <label class="form-label">Email</label>
              <input type="email" class="form-control" v-model="email" required>
            </div>
            <div class="mb-3">
              <label class="form-label">Mật khẩu</label>
              <input type="password" class="form-control" v-model="password" required>
            </div>
            <button type="submit" class="btn btn-primary w-100">Đăng nhập</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>