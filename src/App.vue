<script setup>
import { RouterLink, RouterView } from "vue-router";
import Sidebar from "./components/Sidebar.vue";
import Navbar from "./components/Navbar.vue";
</script>

<template>
  <div class="home">
    <Sidebar />
    <div class="main">
      <Navbar />
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
