<script lang="ts">
export default {
  props: {
    showModal: {
      type: Boolean,
      required: true,
    },
    peopleCount: {
      type: Number,
      required: true,
    },
  },
  methods: {
    closeModal() {
      this.$emit('update:showModal', false)
    },
  },
}
</script>

<template>
  <div class="modal">
    <div class="modal-content">
      <div class="modal-header">
        <div class="modal-header-content">How many people?</div>
        <div class="modal-header-cross-icon" @click="closeModal">
          <i class="fas fa-times"></i>
        </div>
      </div>

      <div class="horizontal-rule">
        <hr />
      </div>

      <div class="modal-input">
        <div class="modal-input-label">
          <p>Enter the number of how many people you want to add to the list.</p>
        </div>

        <!-- <div class="modal-input-field">
            <input type="number" v-model="peopleCount" />
          </div> -->
      </div>

      <div class="horizontal-rule">
        <hr />
      </div>
    </div>

    <div class="modal-buttons">
      <div class="cancel-btn">
        <button @click="closeModal">Cancel</button>
      </div>

      <div class="start-btn">
        <button @click="startGame">Start</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal {
  width: 437px;
  height: 282px;
  top: 22px;
  gap: 0px;
  border-radius: 5px 0px 0px 0px;
  background-color: white;
  position: relative;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  border-radius: 10px;
}

.horizontal-rule {
  hr {
    width: 100%;
    border: 1px solid #cccccc;
  }
}

.modal-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;

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
    color: #999999;
  }
}

.modal-input {
  margin-top: 20px;
  margin-bottom: 50px;

  .modal-input-label {
    p {
      font-size: 14px;
      margin-left: 10px;
      font-weight: 400;
      line-height: 22px;
      color: #555555;
    }
  }

  .modal-input-field {
    input {
      width: 400px;
      height: 40px;
      border: 1px solid #cccccc;
      border-radius: 5px;
      margin-top: 10px;
      padding-left: 14px;
      margin-left: 10px;
    }
  }
}

.modal-buttons {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}

.start-btn {
  button {
    cursor: pointer;
    width: 78px;
    height: 40px;
    background-color: #f68d03;
    color: white;
    border-radius: 10px;
    border-color: transparent;
    font-size: 14px;
    line-height: 18px;
    box-shadow: 0px 1.5px 1.5px rgba(0, 0, 0, 0.25);
  }
}

.cancel-btn {
  button {
    cursor: pointer;
    width: 88px;
    height: 40px;
    background-color: #eeeeee;
    color: #555555;
    border-radius: 10px;
    border-color: transparent;
    font-size: 14px;
    line-height: 18px;
    font-weight: 700;
    box-shadow: 0px 1.5px 1.5px rgba(0, 0, 0, 0.25);
  }
}
</style>
