<template>
  <div>
    <StudentForm @add-student="addStudent" />
    <div>
      <h3>Data Siswa yang Sedang Diinput:</h3>
      <p><strong>Nama:</strong> {{ currentStudent.name }}</p>
      <p><strong>Usia:</strong> {{ currentStudent.age }}</p>
      <p><strong>Gender:</strong> {{ currentStudent.gender }}</p>
      <p><strong>Kelas:</strong> {{ currentStudent.class }}</p>
    </div>
    <StudentList :students="students" />
  </div>
</template>

<script>
import StudentForm from './components/StudentForm.vue';
import StudentList from './components/StudentList.vue';

export default {
  name: 'App',
  components: {
    StudentForm,
    StudentList,
  },
  data() {
    return {
      students: [],
      currentStudent: {
        name: '',
        age: '',
        gender: '',
        class: '',
      },
    };
  },
  methods: {
    addStudent(student) {
      this.students.push(student);
      this.currentStudent = student;
    },
  },
};
</script>

<style>
body {
  font-family: 'Arial', sans-serif;
  background-color: #f9f9f9;
  color: #333;
  margin: 0;
  padding: 0;
  line-height: 1.6;
}

h2, h3 {
  color: #444;
}

.container {
  max-width: 800px;
  margin: 20px auto;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

button {
  background-color: #6c63ff;
  color: white;
  font-size: 16px;
  border: none;
  border-radius: 6px;
  padding: 10px 15px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #5750e8;
}

input, select {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ddd;
  border-radius: 6px;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

input:focus, select:focus {
  border-color: #6c63ff;
  box-shadow: 0 0 5px rgba(108, 99, 255, 0.5);
  outline: none;
}

label {
  font-weight: bold;
  margin-bottom: 5px;
  display: block;
}

ul {
  list-style-type: none;
  padding: 0;
}

.student-list li {
  background-color: #f4f4f4;
  border: 1px solid #ddd;
  border-radius: 6px;
  padding: 10px;
  margin-bottom: 10px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.student-list li:hover {
  transform: scale(1.02);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.student-list strong {
  color: #444;
}

hr {
  border: none;
  border-top: 1px solid #ddd;
  margin: 20px 0;
}

</style>
