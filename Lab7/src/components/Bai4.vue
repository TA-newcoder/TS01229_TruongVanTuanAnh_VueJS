<script setup>
import { ref } from 'vue';

// Import 2 component con vào
import LoginComponent from './LoginComponent.vue';
import CommentComponent from './CommentComponent.vue';

// Biến trạng thái
const isLoggedIn = ref(false);
const loggedInUser = ref('');

// Hàm xử lý khi nhận được sự kiện 'loggedIn' từ con
const handleLoginSuccess = (user) => {
  loggedInUser.value = user;
  isLoggedIn.value = true;
}
</script>

<template>
  <div class="container py-4">
    <LoginComponent 
      v-if="!isLoggedIn" 
      @loggedIn="handleLoginSuccess" 
    />

    <CommentComponent 
      v-else 
      :username="loggedInUser" 
    />
  </div>
</template>