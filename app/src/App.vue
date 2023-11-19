<template>
  <div id="app" class="container-fluid h-100">
    <div class="row h-100">
      <!-- Left Side for Schedule Table -->
      <div class="col-md-6 h-100">
        <ScheduleTable/>
      </div>

      <!-- Right Side for Selector Configuration -->
      <div class="col-md-6 h-100">
        <SelectorSetting/>
      </div>
    </div>
  </div>
</template>

<script>
import ScheduleTable from './components/ScheduleTable.vue'
import SelectorSetting from './components/SelectorSetting.vue'

export default {
  name: 'App',
  components: {
    ScheduleTable,
    SelectorSetting
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container-fluid {
  padding: 15px;
  height: 100%; /* Fill the height of its parent */
}

/* Ensuring the rows and columns also take full height */
.row, .col-md-6 {
  height: 100%;
}

/* Custom Modal Styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1050;
  width: 100%;
  height: 100%;
  overflow: hidden;
  outline: 0;
  display: none;
}

.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1040; /* Backdrop z-index */
  width: 100vw;
  height: 100vh;
  background-color: #000;
}

.modal-dialog {
  position: relative;
  margin: 1.75rem auto;
  pointer-events: none;
  max-width: 500px; /* Adjust as needed */
}

.modal-content {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100%;
  pointer-events: auto;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 0.3rem;
  outline: 0;
}

/* CSS for slide-down and fade-in effect */
.slide-fade-enter-active {
  animation: slide-in 0.3s ease-out forwards;
}

@keyframes slide-in {
  0% {
    transform: translateY(-20px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.slide-fade-leave-active {
  animation: slide-out 0.3s ease-in forwards;
}

@keyframes slide-out {
  0% {
    transform: translateY(0);
    opacity: 1;
  }
  100% {
    transform: translateY(-20px);
    opacity: 0;
  }
}

.modal.show {
  /* This class combination will display the modal */
  display: block;
}
</style>
