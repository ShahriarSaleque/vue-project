<script setup lang="ts">
import { reactive } from 'vue'
import ModalComponent from '@/components/ModalComponent.vue'

const state = reactive({
  showModal: false,
  peopleCount: 20,
})
</script>

<template>
  <div id="app">
    <div class="table">
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
    </div>
    <div v-if="state.showModal" class="modal-overlay">
      <ModalComponent
        :showModal="state.showModal"
        :peopleCount="state.peopleCount"
        @update:showModal="state.showModal = $event"
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

.table {
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
