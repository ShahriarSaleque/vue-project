<script lang="ts">
import type { Person } from '@/views/HomeView.vue'
import type { PropType } from 'vue'

export default {
  props: {
    people: {
      type: Array as PropType<Person[]>,
      required: true,
    },
  },
  methods: {
    onDragStart(person: Person) {
      this.$emit('update:dragStart', person)
    },
    onDrop(person: Person) {
      this.$emit('update:drop', person)
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
      <tr
        v-for="person in people"
        :key="person.id"
        :draggable="true"
        @dragstart="onDragStart(person)"
        @dragover.prevent
        @drop="onDrop(person)"
      >
        <td>{{ person.name }}</td>
        <td>{{ person.email }}</td>
        <td>{{ person.potatoes }}</td>
      </tr>
    </tbody>
  </table>
</template>
