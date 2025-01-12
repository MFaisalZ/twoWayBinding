<template>
    <div class="form-container">
      <h2>Form Data Siswa</h2>
      <div class="form-group">
        <label for="name">Nama:</label>
        <input type="text" id="name" v-model="student.name" placeholder="Masukkan nama siswa" />
      </div>
      <div class="form-group">
        <label for="age">Usia:</label>
        <input type="number" id="age" v-model="student.age" placeholder="Masukkan usia siswa" />
      </div>
      <div class="form-group">
        <label>Gender:</label>
        <label>
          <input type="radio" value="Laki-laki" v-model="student.gender" /> Laki-laki
        </label>
        <label>
          <input type="radio" value="Perempuan" v-model="student.gender" /> Perempuan
        </label>
      </div>
      <div class="form-group">
        <label for="class">Kelas:</label>
        <select id="class" v-model="student.class">
          <option disabled value="">Pilih kelas</option>
          <option>10</option>
          <option>11</option>
          <option>12</option>
        </select>
      </div>
      <button @click="submitForm">Tambah Siswa</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StudentForm',
    data() {
      return {
        student: {
          name: '',
          age: '',
          gender: '',
          class: '',
        },
      };
    },
    methods: {
      submitForm() {
        if (
          this.student.name &&
          this.student.age &&
          this.student.gender &&
          this.student.class
        ) {
          this.$emit('add-student', { ...this.student });
          this.student = { name: '', age: '', gender: '', class: '' };
        } else {
          alert('Mohon isi semua data siswa!');
        }
      },
    },
  };
  </script>
  
  <style scoped>
  /* Tambahkan CSS khusus komponen ini di sini */
  </style>
  