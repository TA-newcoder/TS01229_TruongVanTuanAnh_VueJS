<template>
  <div class="container">
    <h1>Bài 1</h1>

    <p>{{ message }}</p>

    <button @click="updateMessage">Bấm vào đây</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const message = ref('Thông điệp ban đầu');

const updateMessage = () => {
  message.value = 'Thông điệp đã thay đổi!';
};
</script>

<style scoped>
.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: sans-serif;

}

p {
  font-size: 20px;
  margin: 20px 0;
  color: ;
}

button {
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
}
</style>