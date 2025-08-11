<template>
  <div>
    <h1>App.vue</h1>
    <p>ชื่อ: {{ name }}</p>               <!-- แสดงชื่อที่เก็บไว้ใน data -->
    <p>อายุ: {{ age }}</p>                <!-- แสดงอายุที่เก็บไว้ใน data -->

    <!-- ส่ง props ชื่อและอายุไปยัง UserCard component -->
    <!-- รับ event update-name จาก UserCard เพื่ออัปเดตชื่อ -->
    <UserCard :name="name" :age="age" @update-name="handleNameUpdate" />
  </div>
</template>

<script>
import UserCard from './components/UserCard.vue'   // นำเข้า UserCard component

export default {
  components: { UserCard },                        // ลงทะเบียน component UserCard

  data() {
    return {
      name: 'ฮิลมี',        // กำหนดค่าชื่อเริ่มต้น
      age: 25              // กำหนดค่าอายุเริ่มต้น
    }
  },

  methods: {
    // ฟังก์ชันรับค่าใหม่จาก event update-name ที่ส่งมาจาก UserCard
    handleNameUpdate(newName) {
      this.name = newName      // อัปเดตชื่อใหม่ใน data
    }
  }
}
</script>
