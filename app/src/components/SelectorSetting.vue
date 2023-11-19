<template>
  <div class="selector-setting">
    <ul class="nav nav-tabs mb-2">
      <li class="nav-item" v-for="(tab, index) in tabs" :key="index">
        <a class="nav-link" :class="{ active: currentTab === tab }" @click="currentTab = tab">
          <span v-html="tab.icon"></span> {{ tab.title }}
        </a>
      </li>
    </ul>

    <div class="tab-content">
      <component :is="currentTab.component"></component>
    </div>
  </div>
</template>

<script>
import { markRaw } from 'vue';
import MandatoryCourses from './SelectorSetting/MandatoryCourses.vue';
import AllCourses from './SelectorSetting/AllCourses.vue';
import AutoSelect from "@/components/SelectorSetting/AutoSelect.vue";
import CurrentSelected from "@/components/SelectorSetting/CurrentSelected.vue";
import OneClickSelect from "@/components/SelectorSetting/OneClickSelect.vue";
import AppAnnouncement from "@/components/SelectorSetting/AppAnnouncement.vue";
// Import other components

export default {
  name: 'SelectorSetting',
  data() {
    return {
      currentTab: null,
      tabs: [
        {
          title: '所有課程', component: markRaw(AllCourses),
          icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" class="bi bi-file-earmark-plus-fill" viewBox="0 0 16 16">\n' +
              '      <path d="M9.293 0H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h8a2 2 0 0 0 2-2V4.707A1 1 0 0 0 13.707 4L10 .293A1 1 0 0 0 9.293 0zM9.5 3.5v-2l3 3h-2a1 1 0 0 1-1-1zM8.5 7v1.5H10a.5.5 0 0 1 0 1H8.5V11a.5.5 0 0 1-1 0V9.5H6a.5.5 0 0 1 0-1h1.5V7a.5.5 0 0 1 1 0z"/>\n' +
              '  </svg>'
        },
        {title: '本學期必修', component: markRaw(MandatoryCourses),
          icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" class="bi bi-exclamation-diamond-fill" viewBox="0 0 16 16">\n' +
              '      <path d="M9.05.435c-.58-.58-1.52-.58-2.1 0L.436 6.95c-.58.58-.58 1.519 0 2.098l6.516 6.516c.58.58 1.519.58 2.098 0l6.516-6.516c.58-.58.58-1.519 0-2.098L9.05.435zM8 4c.535 0 .954.462.9.995l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 4.995A.905.905 0 0 1 8 4zm.002 6a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>\n' +
              '  </svg>'
        },
        {title: '自動選課 (Beta)', component: markRaw(AutoSelect),
          icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" class="bi bi-dice-6-fill" viewBox="0 0 16 16">\n' +
              '      <path d="M3 0a3 3 0 0 0-3 3v10a3 3 0 0 0 3 3h10a3 3 0 0 0 3-3V3a3 3 0 0 0-3-3H3zm1 5.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm8 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm1.5 6.5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zM12 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zM5.5 12a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zM4 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>\n' +
              '  </svg>'
        },
        {title: '已選課程', component:markRaw(CurrentSelected),
          icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" class="bi bi-bookmark-check-fill" viewBox="0 0 16 16">\n' +
              '      <path fill-rule="evenodd" d="M2 15.5V2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v13.5a.5.5 0 0 1-.74.439L8 13.069l-5.26 2.87A.5.5 0 0 1 2 15.5zm8.854-9.646a.5.5 0 0 0-.708-.708L7.5 7.793 6.354 6.646a.5.5 0 1 0-.708.708l1.5 1.5a.5.5 0 0 0 .708 0l3-3z"/>\n' +
              '  </svg>'
        },
        {title: '一鍵登記 (JS)', component: markRaw(OneClickSelect),
          icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" class="bi bi-bookmark-check-fill" viewBox="0 0 16 16">\n' +
              '      <path fill-rule="evenodd" d="M2 15.5V2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v13.5a.5.5 0 0 1-.74.439L8 13.069l-5.26 2.87A.5.5 0 0 1 2 15.5zm8.854-9.646a.5.5 0 0 0-.708-.708L7.5 7.793 6.354 6.646a.5.5 0 1 0-.708.708l1.5 1.5a.5.5 0 0 0 .708 0l3-3z"/>\n' +
              '  </svg>'
        },
        {title: '公告', component: markRaw(AppAnnouncement),
          icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" class="bi bi-megaphone-fill" viewBox="0 0 16 16">\n' +
              '      <path d="M13 2.5a1.5 1.5 0 0 1 3 0v11a1.5 1.5 0 0 1-3 0v-11zm-1 .724c-2.067.95-4.539 1.481-7 1.656v6.237a25.222 25.222 0 0 1 1.088.085c2.053.204 4.038.668 5.912 1.56V3.224zm-8 7.841V4.934c-.68.027-1.399.043-2.008.053A2.02 2.02 0 0 0 0 7v2c0 1.106.896 1.996 1.994 2.009a68.14 68.14 0 0 1 .496.008 64 64 0 0 1 1.51.048zm1.39 1.081c.285.021.569.047.85.078l.253 1.69a1 1 0 0 1-.983 1.187h-.548a1 1 0 0 1-.916-.599l-1.314-2.48a65.81 65.81 0 0 1 1.692.064c.327.017.65.037.966.06z"/>\n' +
              '  </svg>'
        },
      ]
    };
  },
  created() {
    // Set default tab
    this.currentTab = this.tabs[0];
  }
};
</script>

<style>
/* Custom Styles for Nav Tabs */
.nav-tabs {
  flex-wrap: wrap; /* Allows the tabs to wrap onto multiple lines */
  border-bottom: 2px solid #dee2e6;
}

.nav-item {
  font-size: 15px;
}

.nav-link {

  border: 1px solid transparent;
  border-radius: 5px; /* Rounded corners for the tabs */
  color: #495057; /* Color for the tab text */
  padding: 7px 15px; /* Padding for larger tab area */
  transition: all 0.3s ease; /* Smooth transition for hover effect */
}

.nav-link:hover {
  color: #491b48;
  background-color: #e2e6ea;
  border-color: #dae0e5;
}

.nav-link.active {
  color: #fff !important;
  background-color: #491b48 !important;
  border-color: #491b48;
}

.nav-link svg {
  padding-right: 5px;
  fill: #7a86ff; /* Use the text color for the SVG */
  transition: fill 0.3s ease; /* Smooth transition for color change */
}

.nav-link.active svg {
  fill: #fff; /* White color for SVG when tab is active */
}
</style>

