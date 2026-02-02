<script setup>
import { ref } from 'vue';

// Khởi tạo biến điểm với giá trị mặc định là 9
const diem = ref(9);
</script>

<template>
  <div class="bai1-container">
    <h3>Nhập điểm của bạn:</h3>
    
    <input 
      type="number" 
      v-model="diem" 
      step="0.1" 
      min="0" 
      max="10"
      placeholder="Nhập điểm..."
    >

    <div class="ket-qua">
      <span v-if="diem >= 9">Xuất sắc</span>
      <span v-else-if="diem >= 8">Giỏi</span>
      <span v-else-if="diem >= 6.5">Khá</span>
      <span v-else-if="diem >= 5">Trung bình</span>
      <span v-else>Yếu</span>
    </div>
  </div>
</template>

<style scoped>
.bai1-container {
  border: 1px solid #ddd;
  padding: 20px;
  border-radius: 8px;
  max-width: 300px;
  font-family: Arial, sans-serif;
}

input {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  box-sizing: border-box; /* Để padding không làm vỡ layout */
}

.ket-qua {
  font-weight: bold;
  font-size: 1.2em;
  color: #2c3e50;
}
</style>