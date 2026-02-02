<script setup>
import { ref } from 'vue';

import Bai1 from './components/Bai1.vue'; // Bài 1: Quản lý công việc
import Bai2 from './components/Bai2.vue'; // Bài 2: Form Đăng nhập
import Bai3 from './components/Bai3.vue'; // Bài 3: Form Đăng ký
import Bai4 from './components/Bai4.vue'; // Bài 4: Hệ thống Bình luận

const currentTab = ref(1);
</script>

<template>
  <div class="container py-4">
    <header class="text-center mb-5">
      <h1 class="fw-bold text-primary text-uppercase"> Lab 7 - VueJS</h1>
      <p class="text-muted">Event Handling & Form Binding & Components</p>
    </header>

    <div class="d-flex justify-content-center flex-wrap gap-2 mb-4">
      <button 
        class="btn" 
        :class="currentTab === 1 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 1"
      >
        Bài 1: Quản lý công việc
      </button>

      <button 
        class="btn" 
        :class="currentTab === 2 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 2"
      >
        Bài 2: Đăng nhập
      </button>

      <button 
        class="btn" 
        :class="currentTab === 3 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 3"
      >
        Bài 3: Đăng ký
      </button>

      <button 
        class="btn" 
        :class="currentTab === 4 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 4"
      >
        Bài 4: Bình luận (Component)
      </button>
    </div>

    <div class="content-display p-4 border rounded shadow-sm bg-white">
      <Bai1 v-if="currentTab === 1" />
      <Bai2 v-if="currentTab === 2" />
      <Bai3 v-if="currentTab === 3" />
      <Bai4 v-if="currentTab === 4" />
    </div>

  </div>
</template>

<style>
body {
  background-color: #f0f2f5;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.content-display {
  min-height: 400px; 
}
</style>