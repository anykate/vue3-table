<script setup>
import { computed, ref } from 'vue'
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
const searchQuery = ref('')
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

const filteredList = computed(() => {
  return updatedList.value.filter((student) => {
    return (
      // converts the query and value to lower case index
      student.Name.toLowerCase().indexOf(searchQuery.value.toLowerCase()) != -1
    )
  })
})
</script>

<template>
  <div class="searchBar mt-5">
    <!-- Filter Search -->
    <div class="input-group mb-5">
      <input
        type="search"
        class="form-control"
        v-model="searchQuery"
        placeholder="Student's Name"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
      />
    </div>
  </div>
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
      <tr v-for="student of filteredList" :key="student.ID">
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
