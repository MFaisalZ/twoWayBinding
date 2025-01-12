<template>
    <div class="student-list">
      <h3>Daftar Siswa:</h3>
      <ul>
        <li v-for="(s, index) in students" :key="index">
          <strong>Nama:</strong> {{ s.name }}<br />
          <strong>Usia:</strong> {{ s.age }}<br />
          <strong>Gender:</strong> {{ s.gender }}<br />
          <strong>Kelas:</strong> {{ s.class }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StudentList',
    props: {
      students: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  /* Tambahkan CSS khusus komponen ini di sini */
  </style>
  