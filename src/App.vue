<script setup>
import Table from './components/Table.vue'
const studentData = [
  {
    ID: '01',
    Name: 'Abiola Esther',
    Course: 'Computer Science',
    Gender: 'Female',
    Age: '22',
  },
  {
    ID: '02',
    Name: 'Robert V. Kratz',
    Course: 'Philosophy',
    Gender: 'Male',
    Age: '20',
  },
  {
    ID: '03',
    Name: 'Kristen Anderson',
    Course: 'Economics',
    Gender: 'Female',
    Age: '21',
  },
  {
    ID: '04',
    Name: 'Adam Simon',
    Course: 'Food science',
    Gender: 'Male',
    Age: '17',
  },
  {
    ID: '05',
    Name: 'Daisy Katherine',
    Course: 'Business studies',
    Gender: 'Female',
    Age: '19',
  },
]
const fields = ['ID', 'Name', 'Course', 'Gender', 'Age']
</script>

<template>
  <div class="container table-responsive">
    <Table :fields="fields" :student-data="studentData" />
  </div>
</template>

<style></style>
