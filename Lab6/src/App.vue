<script setup>
import { ref } from 'vue';

import Bai1 from './components/Bai1.vue';
import Bai2 from './components/Bai2.vue';
import Bai3 from './components/Bai3.vue';
import Bai4 from './components/Bai4.vue';

const currentTab = ref(1);
</script>

<template>
  <div class="container py-4">
    <header class="mb-4 text-center">
      <h1 class="text-primary fw-bold">LAB 6 - VUEJS</h1>
      <p>Chọn bài tập bên dưới để xem chi tiết</p>
    </header>

    <div class="d-flex justify-content-center gap-2 mb-4">
      <button 
        class="btn" 
        :class="currentTab === 1 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 1"
      >
        Bài 1 (Điểm số)
      </button>

      <button 
        class="btn" 
        :class="currentTab === 2 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 2"
      >
        Bài 2 (Mùa)
      </button>

      <button 
        class="btn" 
        :class="currentTab === 3 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 3"
      >
        Bài 3 (List Bài viết)
      </button>

      <button 
        class="btn" 
        :class="currentTab === 4 ? 'btn-primary' : 'btn-outline-primary'"
        @click="currentTab = 4"
      >
        Bài 4 (CRUD Học sinh)
      </button>
    </div>

    <div class="content-area p-4 border rounded shadow-sm bg-white">
      <Bai1 v-if="currentTab === 1" />
      <Bai2 v-if="currentTab === 2" />
      <Bai3 v-if="currentTab === 3" />
      <Bai4 v-if="currentTab === 4" />
    </div>

  </div>
</template>

<style>
body {
  background-color: #f8f9fa;
}

.content-area {
  min-height: 400px;
}
</style>