<template>
  <transition name="slide-fade">
    <div v-if="showModal" class="modal show d-block" tabindex="-1" role="dialog">
      <!-- Modal content -->
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="DeleteCourseConfirmTitle">⚠️ 注意</h5>
            <button type="button" class="close border-0 bg-transparent fs-2 text-secondary" @click="showModal = false" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <span class="fw-bold fs-5">確定要刪除所選課程嗎？</span>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" @click="showModal = false">取消</button>
            <button type="button" class="btn btn-light style-btn" style="background-color: #9c4b4b;" @click="deleteCourses">
              <span>全部刪除</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </transition>

  <!-- Backdrop -->
  <div v-if="showModal" class="modal-backdrop show"></div>

  <div class="current-select">
    <!-- Content for 已選課程 -->
    <div class="header">
      <div class="all-credits-cell">已選學分：
        <span id="all_credits">32</span>
      </div>
      <div class="all-credits-cell">總時數：
        <span id="tt_time">32</span>
      </div>
      <!-- Trigger Button for Modal -->
      <div class="delete-button">
        <button type="button" class="btn btn-light style-btn" @click="showModal = true">
          <span>全部刪除</span>
        </button>
      </div>
    </div>
  </div>

  <div class="list_container" style="max-height: 700px; overflow: auto;">
    <table class="table table-bordered border-white border-5 rounded-5 table-secondary">
      <thead>
      <tr class="align-middle">
        <th class="header-cell" style="width:5%;">選擇</th>
        <th class="header-cell" style="width:17%;">課程名稱</th>
        <th class="header-cell" style="width:6%;">時間</th>
        <th class="header-cell" style="width:5%;">班級</th>
        <th class="header-cell" style="width:10%;">上課系所</th>
        <th class="header-cell" style="width:3%;">必選</th>
        <th class="header-cell" style="width:3%;">學分</th>
        <th class="header-cell" style="width:13%;">授課教師</th>
        <th class="header-cell" style="width:13%;">所屬學程</th>
        <th class="header-cell" style="width:5%;">英文授課</th>
        <th class="header-cell" style="width:10%;">教室</th>
        <th class="header-cell" style="width:10%;">課號</th>
      </tr>
      </thead>
      <tbody>
      <!-- Data rows will go here -->
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'CurrentSelect',
  data() {
    return {
      showModal: false
    };
  },
  methods: {
    deleteCourses() {
      // Logic to delete courses
      this.showModal = false;
    }
  }
};
</script>

<style>
/* Styles for this component */
.current-select {
  .header {
    display: block;
    padding: 10px 0 5px 28px;
  }

  .all-credits-cell {
    display: inline-block;
    font-weight: normal;
    font-size: 16px;
    padding-left: 5px;
  }

  #all_credits, #tt_time {
    font-weight: bold;
    background-color: #e0e8f0 !important;
    padding: 5px;
    border-radius: 3px;
  }

  .delete-button {
    padding-top: 10px;
  }
}

.style-btn {
  color: #fff;
  border-color: #9c4b4b;
  background-color: #9c4b4b !important;
  font-weight: bold;
}

.style-btn:hover {
  color: #9c4b4b !important;
  background-color: #fff !important;
}

.header-cell {
  border-radius: 10%;
  background-color: lightgray !important;
}
</style>