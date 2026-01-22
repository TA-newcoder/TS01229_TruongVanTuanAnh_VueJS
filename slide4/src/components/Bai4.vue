<script setup>
// Khai báo mảng dữ liệu bài viết
const items = [
  { 
    title: '8 loại rau củ quả giàu canxi', 
    content: 'Canxi là khoáng chất cần thiết cho cơ thể, giúp xương chắc khỏe...', 
    image: 'https://images.unsplash.com/photo-1540420773420-3366772f4999?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&w=400'
  },
  { 
    title: 'Các loại gia vị tốt cho sức khỏe', 
    content: 'Một số loại gia vị như nghệ, gừng, tỏi không chỉ tạo hương vị...', 
    image: 'https://images.unsplash.com/photo-1596040033229-a9821ebd058d?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&w=400' 
  },
  { 
    title: '9 loại đậu bổ dưỡng nên dùng', 
    content: 'Đậu lăng, đậu nành, đậu phộng chứa nhiều protein thực vật...', 
    image: 'https://images.unsplash.com/photo-1515543904379-3d757afe72e3?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&w=400' 
  }
];
</script>

<template>
  <div class="container mt-5">
    <h1 class="text-center text-primary mb-4">Kiến thức sức khỏe cộng đồng</h1>
    
    <div class="row">
      <div class="col-sm-4">
        <div class="card h-100">
          <img :src="items[0].image" class="card-img-top" alt="Hình ảnh" style="height: 200px; object-fit: cover;" />
          <div class="card-body">
            <h5 class="card-title">{{ items[0].title }}</h5>
            <p class="card-text">{{ items[0].content }}</p>
            <button class="btn btn-info text-white">Xem chi tiết</button>
          </div>
        </div>
      </div>

      <div class="col-sm-4">
        <div class="card h-100">
          <img :src="items[1].image" class="card-img-top" alt="Hình ảnh" style="height: 200px; object-fit: cover;" />
          <div class="card-body">
            <h5 class="card-title">{{ items[1].title }}</h5>
            <p class="card-text">{{ items[1].content }}</p>
            <button class="btn btn-info text-white">Xem chi tiết</button>
          </div>
        </div>
      </div>

      <div class="col-sm-4">
        <div class="card h-100">
          <img :src="items[2].image" class="card-img-top" alt="Hình ảnh" style="height: 200px; object-fit: cover;" />
          <div class="card-body">
            <h5 class="card-title">{{ items[2].title }}</h5>
            <p class="card-text">{{ items[2].content }}</p>
            <button class="btn btn-info text-white">Xem chi tiết</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Thêm style nếu cần */
</style>