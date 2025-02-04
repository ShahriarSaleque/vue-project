<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'SuccessModal',
  props: {
    showModal: {
      type: Boolean,
      required: true,
    },
    timer: {
      type: Number,
      required: true,
    },
  },
  methods: {
    closeModal() {
      this.$emit('update:show', false)
    },
  },
})
</script>

<template>
  <transition name="modal">
    <div class="modal-overlay" v-if="showModal">
      <div class="modal">
        <div class="modal-header">
          <img
            src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNGxmanFxZHRsY3MwOGVmcmxhZHpwaGV5azEycWtrem00MzhlMzdtcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Q81NcsY6YxK7jxnr4v/giphy.gif"
            alt="Success"
            class="modal-gif"
          />
        </div>
        <div class="modal-body">
          <p class="success-message">Success! Your score is {{ timer }} seconds.</p>
        </div>
        <div class="modal-footer">
          <div class="cancel-btn">
            <button @click="closeModal">Close</button>
          </div>
        </div>
      </div>
    </div>
  </transition>
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
  background-color: white;
  border-radius: 10px;
  width: 437px;
  padding: 20px;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.modal-gif {
  width: 200px;
  height: auto;
}

.modal-body {
  flex: 1;
  padding: 20px 0;
}

.modal-footer {
  display: flex;
  justify-content: flex-end;
}

.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.5s;
}

.success-message {
  font-family: 'Roboto', sans-serif;
  font-size: 20px;
  margin-bottom: 20px;
}

.modal-enter,
.modal-leave-to {
  opacity: 0;
}

.cancel-btn {
  button {
    cursor: pointer;
    width: 70px;
    height: 30px;
    background-color: #f68d03;
    color: white;
    border-radius: 10px;
    border-color: transparent;
    font-size: 14px;
    line-height: 18px;
    box-shadow: 0px 1.5px 1.5px rgba(0, 0, 0, 0.25);
  }
}
</style>
