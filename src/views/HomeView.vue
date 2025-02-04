<script setup lang="ts">
import { reactive } from 'vue'
import { faker } from '@faker-js/faker'

import ModalComponent from '@/components/ModalComponent.vue'
import TableComponent from '@/components/TableComponent.vue'

export type Person = {
  id: number
  name: string
  email: string
  potatoes: number
}

const state = reactive({
  showModal: false,
  peopleCount: 20,
  people: [] as Array<Person>,
  gameStarted: false,
  draggingPerson: null as Person | null,
})

const startGame = () => {
  // make sure the people count is between 20 and 100
  if (state.peopleCount < 20 || state.peopleCount > 100) {
    alert('Please enter a number between 20 and 100')
    return
  }

  generatePeople()

  // close the modal
  state.showModal = false
  state.gameStarted = true
}

const generatePeople = () => {
  // randomly generate and asign people
  state.people = Array.from({ length: state.peopleCount }, (_, i) => ({
    id: i,
    name: faker.person.fullName(),
    email: faker.internet.email(),
    potatoes: i + 1,
  })).sort(() => Math.random() - 0.5)
}

const dropEvent = (targetPerson: Person) => {
  console.log('drop', targetPerson)

  if (state.draggingPerson) {
    const draggingIndex = state.people.indexOf(state.draggingPerson)
    const targetIndex = state.people.indexOf(targetPerson)

    // swap the person in dragging index with the person in target index
    state.people.splice(draggingIndex, 1)
    state.people.splice(targetIndex, 0, state.draggingPerson)
  }
}
</script>

<template>
  <div id="app">
    <div class="table-component">
      <div class="table-header">
        <div class="table-header-content">
          <p>Sorting Training System</p>
        </div>
        <div class="table-header-content">
          <div class="table-header-content-button">
            <button @click="state.showModal = true">Start sorting!</button>
          </div>
        </div>
      </div>

      <div v-if="state.gameStarted">
        <TableComponent
          :people="state.people"
          @update:dragStart="state.draggingPerson = $event"
          @update:drop="dropEvent($event)"
        />
      </div>
    </div>

    <div v-if="state.showModal" class="modal-overlay">
      <ModalComponent
        :showModal="state.showModal"
        :peopleCount="state.peopleCount"
        @update:showModal="state.showModal = $event"
        @update:peopleCount="state.peopleCount = $event"
        @update:startGame="startGame"
      />
    </div>
  </div>
</template>

<style scoped>
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.table-component {
  font-family: Roboto;

  .table-header {
    display: flex;
    justify-content: space-between;

    .table-header-content {
      p {
        font-family: 'Roboto', sans-serif;
        font-size: 25px;
        font-weight: 700;
        line-height: 37px;
        text-align: left;
      }
    }

    .table-header-content-button {
      button {
        font-family: 'Roboto', sans-serif;
        cursor: pointer;
        border-radius: 10px;
        background-color: #ff8d00;
        border-color: transparent;
        color: white;
        font-size: 16px;
        line-height: 20px;
        box-shadow: 0px 1.5px 1.5px rgba(0, 0, 0, 0.25);
        padding: 12px;
        position: relative;
        top: 20px;
      }
    }
  }
}
</style>
