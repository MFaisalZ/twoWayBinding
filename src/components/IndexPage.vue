<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Form Data Siswa</title>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      padding: 0;
    }
    .form-container {
      margin-bottom: 20px;
    }
    .form-group {
      margin-bottom: 15px;
    }
    label {
      display: block;
      font-weight: bold;
      margin-bottom: 5px;
    }
    input, select, button {
      width: 100%;
      padding: 10px;
      margin: 5px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      background-color: #28a745;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #218838;
    }
    .student-list {
      margin-top: 20px;
    }
    .student-list ul {
      list-style-type: none;
      padding: 0;
    }
    .student-list li {
      background: #f8f9fa;
      margin-bottom: 10px;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 4px;
    }
  </style>
</head>
<body>
  <div id="app">
    <div class="form-container">
      <h2>Form Data Siswa</h2>
      <div class="form-group">
        <label for="name">Nama:</label>
        <input type="text" id="name" v-model="student.name" placeholder="Masukkan nama siswa">
      </div>
      <div class="form-group">
        <label for="age">Usia:</label>
        <input type="number" id="age" v-model="student.age" placeholder="Masukkan usia siswa">
      </div>
      <div class="form-group">
        <label>Gender:</label>
        <label>
          <input type="radio" value="Laki-laki" v-model="student.gender"> Laki-laki
        </label>
        <label>
          <input type="radio" value="Perempuan" v-model="student.gender"> Perempuan
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
      <button @click="addStudent">Tambah Siswa</button>
    </div>

    <div>
      <h3>Data Siswa yang Sedang Diinput:</h3>
      <p><strong>Nama:</strong> {{ student.name }}</p>
      <p><strong>Usia:</strong> {{ student.age }}</p>
      <p><strong>Gender:</strong> {{ student.gender }}</p>
      <p><strong>Kelas:</strong> {{ student.class }}</p>
    </div>

    <div class="student-list">
      <h3>Daftar Siswa:</h3>
      <ul>
        <li v-for="(s, index) in students" :key="index">
          <strong>Nama:</strong> {{ s.name }}<br>
          <strong>Usia:</strong> {{ s.age }}<br>
          <strong>Gender:</strong> {{ s.gender }}<br>
          <strong>Kelas:</strong> {{ s.class }}
        </li>
      </ul>
    </div>
  </div>

  <script>
    new Vue({
      el: '#app',
      data: {
        student: {
          name: '',
          age: '',
          gender: '',
          class: ''
        },
        students: []
      },
      methods: {
        addStudent() {
          if (this.student.name && this.student.age && this.student.gender && this.student.class) {
            this.students.push({ ...this.student });
            this.student = { name: '', age: '', gender: '', class: '' };
          } else {
            alert('Mohon isi semua data siswa!');
          }
        }
      }
    });
  </script>
</body>
</html>
