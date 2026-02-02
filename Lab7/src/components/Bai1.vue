<script setup>
import { ref } from 'vue';

// 1. Biến lưu tên công việc đang nhập
const newToDo = ref('');

// 2. Mảng chứa danh sách công việc mẫu
const jobs = ref(['Ăn sáng', 'Đi học', 'Chơi bóng rổ']);

// 3. Hàm thêm công việc
const addList = () => {
  if (newToDo.value.trim()) {
    jobs.value.push(newToDo.value.trim());
    newToDo.value = ''; // Reset ô nhập liệu
  }
}

// 4. Hàm xóa công việc
const removeList = (index) => {
  jobs.value.splice(index, 1);
}
</script>

<template>
  <div class="d-flex justify-content-center mt-5">
    <div class="card p-3 shadow-sm" style="width: 400px;">
      
      <h3 class="text-center fw-bold mb-3">Quản lý công việc</h3>
      
      <form @submit.prevent="addList">
        <div class="mb-3">
          <label class="form-label">Tên công việc:</label>
          <input 
            type="text" 
            class="form-control" 
            v-model="newToDo" 
            placeholder="Nhập tên công việc"
          >
        </div>
        
        <button type="submit" class="btn btn-primary mb-4">
          Thêm công việc
        </button>
      </form>

      <ul class="list-group">
        <li 
          class="list-group-item d-flex justify-content-between align-items-center"
          v-for="(job, index) in jobs" 
          :key="index"
        >
          {{ job }}
          
          <button 
            class="btn btn-danger btn-sm" 
            @click="removeList(index)"
          >
            Xóa
          </button>
        </li>
      </ul>
      
    </div>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #dee2e6;
  border-radius: 8px;
}

.list-group-item {
  padding-top: 12px;
  padding-bottom: 12px;
}
</style>
