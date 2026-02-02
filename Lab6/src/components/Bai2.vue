<script setup>
import { ref } from 'vue';

// Khởi tạo tháng mặc định là 1
const month = ref(1);
</script>

<template>
  <div class="bai2-container">
    <h3>Nhập tháng của bạn:</h3>
    
    <input 
        type="number" 
        v-model.number="month" 
        placeholder="Nhập tháng..."
    >

    <p v-if="month < 1 || month > 12" style="color: red; font-weight: bold;">
        Vui lòng nhập tháng từ 1 đến 12!
    </p>

    <p v-else-if="month >= 1 && month <= 3" class="season text-green">
        Mùa Xuân
    </p>

    <p v-else-if="month <= 6" class="season text-red">
        Mùa Hè
    </p>

    <p v-else-if="month <= 9" class="season text-orange">
        Mùa Thu
    </p>

    <p v-else class="season text-blue">
        Mùa Đông
    </p>
  </div>
</template>

<style scoped>
.bai2-container {
    border: 1px solid #ddd;
    padding: 20px;
    border-radius: 8px;
    max-width: 350px;
    font-family: Arial, sans-serif;
    margin-top: 20px; /* Cách bài 1 ra một chút nếu hiển thị cùng lúc */
}

input {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    box-sizing: border-box;
}

.season {
    font-size: 1.2em;
    font-weight: bold;
}

/* Thêm chút màu sắc cho sinh động */
.text-green { color: green; }
.text-red { color: red; }
.text-orange { color: orange; }
.text-blue { color: blue; }
</style>