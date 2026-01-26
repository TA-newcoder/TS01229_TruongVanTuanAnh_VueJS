<script setup>
import { ref } from 'vue';

// Import tất cả các bài tập
import Bai1 from './components/Bai1.vue';
import Bai2 from './components/Bai2.vue';
import Bai3 from './components/Bai3.vue';
import Bai4 from './components/Bai4.vue';

// Biến này lưu trạng thái bài nào đang được chọn (mặc định là bài 4)
const currentLesson = ref(4);
</script>

<template>
  <div class="app-wrapper">
    <div class="nav-bar">
      <button @click="currentLesson = 1" :class="{ active: currentLesson === 1 }">Bài 1</button>
      <button @click="currentLesson = 2" :class="{ active: currentLesson === 2 }">Bài 2</button>
      <button @click="currentLesson = 3" :class="{ active: currentLesson === 3 }">Bài 3</button>
      <button @click="currentLesson = 4" :class="{ active: currentLesson === 4 }">Bài 4</button>
    </div>

    <div class="content-area">
      <Bai1 v-if="currentLesson === 1" />
      <Bai2 v-if="currentLesson === 2" />
      <Bai3 v-if="currentLesson === 3" />
      <Bai4 v-if="currentLesson === 4" />
    </div>
  </div>
</template>

<style>
/*  Menu */
.nav-bar {
  display: flex;
  justify-content: center;
  gap: 10px;
  padding: 20px;
  background-color: #333;
  position: sticky;
  top: 0;
  z-index: 100;
}

.nav-bar button {
  padding: 10px 20px;
  border: none;
  background-color: #555;
  color: white;
  cursor: pointer;
  border-radius: 5px;
  font-weight: bold;
}

.nav-bar button:hover {
  background-color: #777;
}

/* Nút đang được chọn sẽ có màu xanh */
.nav-bar button.active {
  background-color: #42b883;
}

.content-area {
  padding: 20px;
  background: #f4f4f4;
  min-height: 100vh;
}

body { margin: 0; padding: 0; font-family: sans-serif; }
</style>