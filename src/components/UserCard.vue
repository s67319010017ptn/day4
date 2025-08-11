<template>
  <div class="user-card">
    <h2>UserCard.vue</h2>
    <p>ชื่อที่ได้รับ: {{ name }}</p>       <!-- แสดงชื่อที่รับมาจาก props -->
    <p>อายุที่ได้รับ: {{ age }}</p>         <!-- แสดงอายุที่รับมาจาก props -->

    <!-- ปุ่มกดเพื่อเปลี่ยนชื่อ -->
    <button @click="changeName">เปลี่ยนชื่อ</button>
  </div>
</template>

<script>
export default {
  props: {
    name: String,     // ประกาศ props ชื่อ เป็น String
    age: Number       // ประกาศ props อายุ เป็น Number
  },

  methods: {
    // ฟังก์ชันเปลี่ยนชื่อที่เรียกเมื่อกดปุ่ม
    changeName() {
      // เปิด prompt ให้ผู้ใช้กรอกชื่อใหม่ โดยแสดงชื่อเดิมเป็นค่าเริ่มต้น
      const newName = prompt('กรุณาใส่ชื่อใหม่:', this.name)

      // ตรวจสอบว่าผู้ใช้ใส่ชื่อใหม่และไม่ใช่ค่าว่าง
      if (newName && newName.trim() !== '') {
        // ส่ง event ชื่อ 'update-name' พร้อมข้อมูลชื่อใหม่กลับไปยัง parent (App.vue)
        this.$emit('update-name', newName.trim())
      }
    }
  }
}
</script>

<style scoped>
.user-card {
  border: 1px solid #ccc;      /* เส้นกรอบสีเทา */
  padding: 1rem;               /* ช่องว่างรอบด้านใน */
  margin-top: 1rem;            /* ช่องว่างด้านบน */
}
button {
  cursor: pointer;             /* เปลี่ยน cursor เมื่อชี้ที่ปุ่ม */
  background-color: #4caf50;   /* สีเขียวปุ่ม */
  color: white;                /* สีตัวอักษรปุ่ม */
  border: none;                /* ไม่มีเส้นขอบ */
  padding: 0.5rem 1rem;        /* ช่องว่างในปุ่มแนวตั้งและแนวนอน */
  border-radius: 4px;          /* มุมปุ่มโค้งมน */
}
button:hover {
  background-color: #45a049;   /* สีปุ่มเมื่อ hover */
}
</style>
