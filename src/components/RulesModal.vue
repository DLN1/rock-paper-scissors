<template>
  <div class="modal-wrapper">
    <div class="modal-container">
      <div class="modal-header">
        <h1>RULES</h1>
        <img @click="$emit('closeModal')" src="@/assets/crossIcon.svg" alt='close modal icon' />
      </div>
      <div class="modal-body">
        <img src="@/assets/rules.svg" alt='rules of rock paper scissors' />
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  height: 100vh !important;
  width: 100vw !important;
  background: rgba(0, 0, 0, 0.364);
  color: #3b4262;
  top: 0;
  left: 0;
  padding: 4rem;
  z-index: 3;
}

.modal-container {
  background: white;
  width: 100%;
  padding: 2rem;
  border-radius: 8px;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.modal-header > img {
    cursor: pointer;
}

.modal-body {
  display: flex;
  margin-top: 2rem;
  justify-content: center;
  width: 100%;
}

.modal-body > img {
  width: 70%;
}

@media (min-width: 768px) {
  .modal-container {
    height: 50%;
    width: 50%;
  }
}
</style>
