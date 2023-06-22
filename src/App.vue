<template>
  <!-- Begin page -->
  <div id="layout-wrapper" :class="{'right-bar-enabled':show, 'sidebar-enable':showL}">
    <HeaderTop @showMenuRight="showMenuRight" @handleLeft="showMenuLeft"/>

    <!-- ========== Left Sidebar Start ========== -->
    <LeftSidebar />
    <!-- Left Sidebar End -->

    <!-- Start right Content here -->
    <MainContent />
    <!-- end main content-->
  
  <!-- END layout-wrapper -->

  <!-- Right Sidebar -->
  <RightBar @close="show=false" />
  <!-- /Right-bar -->

  <!-- Right bar overlay-->
  <div class="rightbar-overlay" @click="show=false"></div>
</div>
</template>

<script>
// import $ from 'jquery'

import HeaderTop from "./components/HeaderTop.vue";
import LeftSidebar from "./components/LeftSidebar.vue";
import MainContent from "./components/MainContent.vue";
import RightBar from "./components/RightBar.vue";

export default {

  name: "App",
  components: {
    HeaderTop,
    LeftSidebar,
    MainContent,
    RightBar,
  },
    data() {
    return{
      show: false,
      showL: false
    }
  },
  methods: {
    
    showMenuRight() {
      this.show = !this.show;
    },
    showMenuLeft() {
      this.toggleSize();
      this.showL = !this.showL;
      
    },
    toggleSize() {
            const currentSidebarSize = document.body.getAttribute('data-sidebar-size');

      if (window.innerWidth >= 992) {
        if (currentSidebarSize === null || currentSidebarSize === 'lg') {
          document.body.setAttribute('data-sidebar-size', 'sm');
        } else if (currentSidebarSize === 'md') {
          document.body.setAttribute('data-sidebar-size', 'sm');
        } else {
          document.body.setAttribute('data-sidebar-size', 'lg');
        }
      }
    }
  },
  mounted() {
    
  }
};
</script>

<style>
@import "../public/assets/css/bootstrap.min.css";
@import "../public/assets/css/icons.min.css";
@import "../public/assets/css/app.min.css";
</style>
