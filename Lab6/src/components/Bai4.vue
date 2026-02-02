<script setup>
import { ref } from 'vue';

// 1. Dữ liệu mẫu ban đầu
const students = ref([
  { name: 'Nguyễn Chí Hùng', score: 8, dob: '2006-01-01' },
  { name: 'Phạm Thị Lan', score: 9, dob: '2006-05-15' }
]);

// 2. Biến quản lý form và trạng thái
const student = ref({
  name: '',
  score: null,
  dob: ''
});

const isEditing = ref(false);
const editingIndex = ref(null);

// 3. Hàm xử lý Submit Form (Thêm hoặc Cập nhật)
function submitForm() {
  if (isEditing.value) {
    // Logic Cập nhật: Ghi đè thông tin vào vị trí đang sửa
    students.value[editingIndex.value] = { ...student.value };
    
    // Reset trạng thái về ban đầu
    isEditing.value = false;
    editingIndex.value = null;
  } else {
    // Logic Thêm mới: Đẩy đối tượng mới vào mảng
    students.value.push({ ...student.value });
  }
  
  // Xóa trắng form sau khi thực hiện xong
  resetForm();
}

// 4. Hàm chuẩn bị dữ liệu để Sửa
function editStudent(index) {
  // Copy dữ liệu từ dòng được chọn lên form
  student.value = { ...students.value[index] };
  
  // Bật chế độ chỉnh sửa
  isEditing.value = true;
  editingIndex.value = index;
}

// 5. Hàm Xóa học sinh
function deleteStudent(index) {
    // Hỏi xác nhận trước khi xóa (tùy chọn thêm cho an toàn)
    if(confirm('Bạn có chắc muốn xóa học sinh này?')) {
        students.value.splice(index, 1);
    }
}

// 6. Hàm Reset Form
function resetForm() {
  student.value = {
    name: '',
    score: null,
    dob: ''
  };
}
</script>

<template>
  <div class="container mt-4">
    <h1 class="text-center mb-4">Quản lý học sinh (CRUD)</h1>
    
    <div class="row">
      <div class="col-sm-4">
        <h3 class="mb-3">Thêm học sinh</h3>
        
        <form @submit.prevent="submitForm">
          
          <div class="mb-3">
            <label for="name" class="form-label">Họ tên:</label>
            <input 
              type="text" 
              class="form-control" 
              id="name" 
              v-model="student.name" 
              required
              placeholder="Nhập họ tên"
            >
          </div>

          <div class="mb-3">
            <label for="score" class="form-label">Điểm:</label>
            <input 
              type="number" 
              class="form-control" 
              id="score" 
              v-model="student.score" 
              min="0" 
              max="10" 
              required
              placeholder="Nhập điểm (0-10)"
            >
          </div>

          <div class="mb-3">
            <label for="dob" class="form-label">Ngày sinh:</label>
            <input 
              type="date" 
              class="form-control" 
              id="dob" 
              v-model="student.dob" 
              required
            >
          </div>

          <button type="submit" class="btn" :class="isEditing ? 'btn-primary' : 'btn-success'">
            {{ isEditing ? 'Cập nhật' : 'Thêm' }}
          </button>
          
          <button 
            type="button" 
            class="btn btn-secondary ms-2" 
            v-if="isEditing" 
            @click="isEditing = false; resetForm()"
          >
            Hủy
          </button>
        </form>
      </div>

      <div class="col-sm-8">
        <h3 class="mb-3">Danh sách học sinh</h3>
        
        <table class="table table-hover table-bordered">
          <thead class="table-light">
            <tr>
              <th>Họ và tên</th>
              <th>Điểm</th>
              <th>Ngày sinh</th>
              <th>Hành động</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(stu, index) in students" :key="index">
              <td>{{ stu.name }}</td>
              <td>{{ stu.score }}</td>
              <td>{{ stu.dob }}</td>
              <td>
                <button 
                  class="btn btn-warning btn-sm me-2" 
                  @click="editStudent(index)"
                >
                  Sửa
                </button>
                
                <button 
                  class="btn btn-danger btn-sm" 
                  @click="deleteStudent(index)"
                >
                  Xóa
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* CSS tùy chỉnh thêm nếu cần */
</style>