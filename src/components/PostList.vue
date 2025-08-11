<template>
  <div class="post-list">
    <div v-if="loading" class="loading">กำลังโหลดข้อมูล...</div>
    <div v-else-if="error" class="error">เกิดข้อผิดพลาดในการดึงข้อมูล</div>
    <ul v-else>
      <li v-for="post in posts" :key="post.id" class="post-item">
        {{ post.title }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'PostList',
  data() {
    return {
      posts: [],
      loading: false,
      error: false,
    };
  },
  async created() {
    this.loading = true;          // เริ่มโหลดข้อมูล
    this.error = false;           // ล้างสถานะ error
    try {
      const res = await fetch('https://jsonplaceholder.typicode.com/posts');
      if (!res.ok) throw new Error('Network response was not ok');
      this.posts = await res.json();  // ดึงข้อมูล JSON มาเก็บใน posts
    } catch (e) {
      this.error = true;          // เกิดข้อผิดพลาด
      console.error(e);
    } finally {
      this.loading = false;       // โหลดเสร็จแล้ว
    }
  },
};
</script>

<style scoped>
.post-list {
  max-width: 600px;
  margin: 20px auto;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.loading, .error {
  text-align: center;
  font-size: 18px;
  padding: 20px;
  color: #666;
}
.error {
  color: red;
}
ul {
  list-style-type: none;
  padding: 0;
}
.post-item {
  padding: 12px 16px;
  border-bottom: 1px solid #ddd;
}
.post-item:last-child {
  border-bottom: none;
}
</style>
