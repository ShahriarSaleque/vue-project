<script lang="ts">
export default {
  props: {
    people: {
      type: Array,
      required: true,
    },
  },
}
</script>

<template>
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Potatoes</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="person in people" :key="person.id">
        <td>{{ person.name }}</td>
        <td>{{ person.email }}</td>
        <td>{{ person.potatoes }}</td>
      </tr>
    </tbody>
  </table>
</template>
