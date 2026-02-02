<script setup>
import { ref } from 'vue';

// 1. Nhận dữ liệu 'username' từ component cha truyền vào
const props = defineProps(['username']);

const commentText = ref('');
// Mảng chứa các bình luận
const comments = ref([
    { name: 'Binh An', text: 'Bài viết rất hữu ích' } // Dữ liệu mẫu
]);

// 2. Hàm gửi bình luận
const submitComment = () => {
  if (commentText.value) {
    // Thêm bình luận mới vào đầu danh sách
    comments.value.unshift({
      name: props.username, // Lấy tên từ props
      text: commentText.value
    });
    
    // Reset ô nhập
    commentText.value = '';
  }
}
</script>

<template>
  <div class="col-sm-6 mx-auto p-4 border rounded shadow-sm bg-white mt-4">
    <h3 class="fw-bold mb-3">Bình luận bài viết</h3>
    
    <div class="card mb-4">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Good_Food_Display_-_NCI_Visuals_Online.jpg/800px-Good_Food_Display_-_NCI_Visuals_Online.jpg" class="card-img-top" alt="Hình ảnh" style="height: 200px; object-fit: cover;">
      <div class="card-body">
        <h5 class="card-title">8 loại rau củ quả giàu canxi</h5>
        <p class="card-text">Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ sung canxi...</p>
      </div>
    </div>

    <form @submit.prevent="submitComment">
      <div class="mb-3">
        <textarea 
          class="form-control" 
          rows="3" 
          v-model="commentText" 
          placeholder="Nhập bình luận của bạn..."
        ></textarea>
      </div>
      <button type="submit" class="btn btn-success">Gửi bình luận</button>
    </form>

    <div class="mt-4" v-if="comments.length">
      <h5 class="fw-bold">Danh sách các bình luận:</h5>
      <ul class="list-unstyled mt-3">
        <li v-for="(comment, index) in comments" :key="index" class="mb-2 p-2 bg-light rounded">
          <span class="fw-bold">{{ comment.name }}: </span>
          <span>{{ comment.text }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>