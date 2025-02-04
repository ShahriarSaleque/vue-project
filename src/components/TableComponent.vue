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
  <table class="sortable-table">
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

<style scoped>
.sortable-table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0 8px;
  font-family: 'Roboto', sans-serif;
}

.sortable-table thead {
  background-color: #f4f4f4;
  font-weight: bold;
}

.sortable-table th,
.sortable-table td {
  padding: 12px 16px;
  text-align: left;
}

.sortable-table th {
  border-bottom: 2px solid #ddd;
  font-size: 14px;
  color: #333;
}

.sortable-table tbody tr {
  cursor: move;
  background: white;
  border-radius: 6px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: background 0.2s;
}

.sortable-table tbody tr:hover {
  background: #f9f9f9;
}

.sortable-table tbody td {
  border-top: 1px solid #eee;
}

.sortable-table tbody tr:first-child td {
  border-top: none;
}

/* Checkbox styling */
input[type='checkbox'] {
  width: 18px;
  height: 18px;
  border-radius: 4px;
  accent-color: #ff7d30;
}
</style>
