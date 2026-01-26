<template>
    <div class="container">
        <h1>Bài 2: v-model (Two-way binding)</h1>

        <input v-model="userInput" type="text" placeholder="Nhập gì đó đi..." />

        <p>Kết quả: <b>{{ userInput }}</b></p>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const userInput = ref('FPL');
</script>


<style scoped>
.container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

input {
    padding: 10px;
    font-size: 16px;
    margin-bottom: 20px;
    width: 250px;
}

p {
    font-size: 20px;
}
</style>