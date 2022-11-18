<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  fields: {
    type: Array,
  },
  studentData: {
    type: Array,
  },
})
</script>

<template>
  <table class="table caption-top">
    <caption>
      <h1 class="text-center">List of Users</h1>
    </caption>
    <thead>
      <tr>
        <th scope="col" v-for="(field, index) of props.fields" :key="index">
          {{ field }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="student of props.studentData" :key="student.ID">
        <th scope="row">{{ student.ID }}</th>
        <td>{{ student.Name }}</td>
        <td>{{ student.Course }}</td>
        <td>{{ student.Gender }}</td>
        <td>{{ student.Age }}</td>
      </tr>
    </tbody>
  </table>
</template>
