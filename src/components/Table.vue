<script setup>
import { ref } from 'vue'
// Importing the lodash library
import { sortBy } from 'lodash'

const props = defineProps({
  fields: {
    type: Array,
  },
  studentData: {
    type: Array,
  },
})

// a value to check for sort
const sort = ref(true)
const updatedList = ref(props.studentData)
// a function to sort the table
const sortTable = (col) => {
  sort.value = !sort.value
  if (!sort.value) {
    // Use of _.sortBy() method
    updatedList.value = sortBy(props.studentData, col)
  } else {
    updatedList.value = props.studentData
  }
}
</script>

<template>
  <table class="table caption-top">
    <caption>
      <h1 class="text-center">List of Users</h1>
    </caption>
    <thead>
      <tr>
        <th
          scope="col"
          v-for="field of props.fields"
          :key="field"
          @click="sortTable(field)"
        >
          {{ field }}
          <i class="bi bi-sort-alpha-down" aria-label="Sort Icon"></i>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="student of updatedList" :key="student.ID">
        <th scope="row">{{ student.ID }}</th>
        <td>{{ student.Name }}</td>
        <td>{{ student.Course }}</td>
        <td>{{ student.Gender }}</td>
        <td>{{ student.Age }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
table thead th:hover {
  background: #f2f2f2;
}
</style>
