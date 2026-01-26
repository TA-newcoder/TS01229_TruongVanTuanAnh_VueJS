<script setup>
import { reactive } from 'vue';

// Dùng reactive cho đối tượng (Object) thay vì ref
const userInfo = reactive({
  name: '',
  age: null,
  email: ''
});
</script>

<template>
  <div class="container">
    <div class="card">
      <h1>Thông tin cá nhân</h1>
      
      <form @submit.prevent>
        <div class="form-group">
          <label>Họ và Tên:</label>
          <input 
            v-model="userInfo.name" 
            type="text" 
            placeholder="Nhập họ tên..." 
          />
        </div>

        <div class="form-group">
          <label>Tuổi:</label>
          <input 
            v-model="userInfo.age" 
            type="number" 
            placeholder="Nhập tuổi..." 
          />
        </div>

        <div class="form-group">
          <label>Email:</label>
          <input 
            v-model="userInfo.email" 
            type="email" 
            placeholder="Nhập email..." 
          />
        </div>
      </form>

      <div class="info-display">
        <h2>Thông tin đã nhập:</h2>
        <p><strong>Họ và Tên:</strong> {{ userInfo.name }}</p>
        <p><strong>Tuổi:</strong> {{ userInfo.age }}</p>
        <p><strong>Email:</strong> {{ userInfo.email }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f4f4f4; /* Nền xám nhẹ cho trang */
}

.card {
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  width: 400px;
  border: 1px solid #ddd;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.form-group {
  margin-bottom: 15px;
  text-align: left;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
  color: #555;
}

input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box; /* Để padding không làm vỡ layout */
  font-size: 14px;
}

input:focus {
  border-color: #42b883;
  outline: none;
}

/* Style cho khung hiển thị kết quả màu đen */
.info-display {
  margin-top: 25px;
  background-color: #212529; /* Màu đen như mẫu Bootstrap */
  color: white;
  padding: 20px;
  border-radius: 8px;
  text-align: left;
}

.info-display h2 {
  font-size: 18px;
  margin-top: 0;
  margin-bottom: 15px;
  border-bottom: 1px solid #555;
  padding-bottom: 10px;
}

.info-display p {
  margin: 8px 0;
  font-size: 15px;
}
</style>