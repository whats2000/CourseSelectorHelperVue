<template>
  <div class="schedule-table">
    <table class="table table-bordered border-white border-5 rounded-5 table-secondary">
      <thead>
      <tr>
        <th class="header-cell">節\期</th>
        <th class="header-cell" v-for="(d) in weekday" :key="d">{{ d }}</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(timeSlot, index) in timeSlots" :key="index">
        <td class="time-slot-cell">
          <div class="time-slot-key">{{ timeSlot.key }}</div>
          <div class="time-slot-value">{{ timeSlot.value }}</div>
        </td>
        <td v-for="n in columns - 1" :key="n" :id="`${timeSlot.key}${n}`" class="course-cell"></td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ScheduleTable',
  data() {
    return {
      columns: 8, // Total columns
      weekday: [
         '一', '二', '三', '四', '五', '六', '日'
      ],
      timeSlots: [
        { key: 'A', value: '7:00\n~\n7:50' },
        { key: '1', value: '8:10\n~\n9:00' },
        { key: '2', value: '9:10\n~\n10:00' },
        { key: '3', value: '10:10\n~\n11:00' },
        { key: '4', value: '11:10\n~\n12:00' },
        { key: 'B', value: '12:10\n~\n13:00' },
        { key: '5', value: '13:10\n~\n14:00' },
        { key: '6', value: '14:10\n~\n15:00' },
        { key: '7', value: '15:10\n~\n16:00' },
        { key: '8', value: '16:10\n~\n17:00' },
        { key: '9', value: '17:10\n~\n18:00' },
        { key: 'C', value: '18:20\n~\n19:10' },
        { key: 'D', value: '19:15\n~\n20:05' },
        { key: 'E', value: '20:10\n~\n21:00' },
        { key: 'F', value: '21:05\n~\n21:55' }
      ]
    }
  }
};
</script>

<style>
table {
  font-size: 10px;
  text-align: center;
}

.header-cell {
  border-radius: 10%;
  background-color: lightgray !important;
}

.schedule-table {
  overflow-x: auto;
}

.time-slot-cell {
  width: 5%;
  border-radius: 10%;
  background-color: lightgrey !important;
}

.time-slot-key {
  font-weight: bold;
  display: block;
}

.time-slot-value {
  display: block;
}

.course-cell {
  border-radius: 10%;
}
</style>
