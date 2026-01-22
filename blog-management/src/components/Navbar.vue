<script setup>
import { ref, onMounted } from 'vue';
import { useRouter } from 'vue-router'; // Thêm dòng này

const currentUser = ref(null);
const router = useRouter(); // Thêm dòng này

onMounted(() => {
  const user = localStorage.getItem('currentUser');
  if (user) {
    currentUser.value = JSON.parse(user);
  }
});

const logout = () => {
  localStorage.removeItem('currentUser');
  currentUser.value = null;
  router.push('/login');
};
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark mb-4">
    <div class="container">
      <RouterLink class="navbar-brand" to="/">Vue Blog</RouterLink>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
        <span class="navbar-toggler-icon"></span>
      </button>
      
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item" v-if="!currentUser">
            <RouterLink class="nav-link" to="/login">Đăng nhập</RouterLink>
          </li>
          <li class="nav-item" v-if="!currentUser">
            <RouterLink class="nav-link" to="/register">Đăng ký</RouterLink>
          </li>

          <li class="nav-item" v-if="currentUser">
            <span class="nav-link text-warning">Chào, {{ currentUser.username }}</span>
          </li>
          <li class="nav-item" v-if="currentUser">
            <RouterLink class="nav-link" to="/profile">Hồ sơ</RouterLink>
          </li>
          <li class="nav-item" v-if="currentUser">
            <a href="#" class="nav-link" @click.prevent="logout">Đăng xuất</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>