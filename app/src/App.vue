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
</style>
