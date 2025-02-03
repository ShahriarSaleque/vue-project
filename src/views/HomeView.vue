<script setup lang="ts">
import { reactive } from 'vue'
const state = reactive({
  showModal: true,
  peopleCount: 20,
})
</script>

<template>
  <div v-if="state.showModal" class="modal-overlay">
    <div class="modal">
      <div class="modal-content">
        <div class="modal-header">
            <div class="modal-header-content">How many people?</div>
            <div class="modal-header-cross-icon" @click="state.showModal = false">
                <i class="fas fa-times"></i>
            </div>
        </div>

        
        <input type="number" v-model.number="state.peopleCount" min="20" max="100" />
      </div>

      <div class="modal-buttons">
        <div class="start-btn" @click="startGame">
          <button @click="startGame">Start</button>
        </div>
        <div class="cancel-btn">
          <button @click="state.showModal = false">Cancel</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
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

.modal {
  width: 437px;
  height: 282px;
  top: 22px;
  gap: 0px;
  border-radius: 5px 0px 0px 0px;
  opacity: 0px;
  background-color: white;
  position: relative;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  border-radius: 10px;
}

.modal-header {
    display: flex;
    justify-content: space-between;

    .modal-header-content {
        font-size: 20px;
        font-weight: 600;
        line-height: 27px;
    }

    .modal-header-cross-icon {
        cursor: pointer;
        width: 12px;
        height: 12px;
        position: relative;
        top: 8px;

    }
}

.modal-buttons {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}

.start-btn {
  button {
    width: 78px;
    height: 40px;
    top: 244px;
    left: 339px;
    gap: 0px;
    opacity: 0px;
    background-color: #f68d03;
    color: white;
    border-radius: 10px;
  }
}

.cancel-btn {
  button {
    width: 88px;
    height: 40px;
    top: 244px;
    left: 241px;
    gap: 0px;
    opacity: 0px;
    background-color: #eeeeee;
    color: #555555;
    border-radius: 10px;
  }
}
</style>
