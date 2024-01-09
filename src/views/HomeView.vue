<script setup>
import Navbar from "@/components/Navbar.vue";
import Sidebar from "@/components/Sidebar.vue";
import { RouterView } from "vue-router";
import { reactive } from "vue";

const sidebarState = reactive({
  sidebarOpen: true,
});

const toggleSidebar = () => {
  sidebarState.sidebarOpen = !sidebarState.sidebarOpen;
};

const openSidebar = () => {
  sidebarState.sidebarOpen = true;
};
</script>

<template>
  <div class="home">
    <Sidebar
      :sidebarOpen="sidebarState.sidebarOpen"
      @open-sidebar="openSidebar"
    />
    <div class="main">
      <Navbar
        :sidebarOpen="sidebarState.sidebarOpen"
        @toggle-sidebar="toggleSidebar"
      />
      <RouterView />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.home {
  display: flex;
  gap: 24px;
}
</style>
