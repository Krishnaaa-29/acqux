<script setup>
import { Icon } from "@iconify/vue";
import { RouterLink } from "vue-router";

const props = defineProps({
  sidebarOpen: {
    type: Boolean,
    required: true,
  },
});

defineEmits(["open-sidebar"]);
</script>

<template>
  <aside class="container" :class="{ 'close-container': !sidebarOpen }">
    <RouterLink to="/dashboard">
      <div class="logo" :class="{ 'close-logo': !sidebarOpen }">
        <img src="../assets/logo.svg" alt="logo" />
        <div class="logo-title">SuprComm</div>
        <Icon
          icon="ep:d-arrow-right"
          width="32"
          height="32"
          class="open-sidebar-icon"
          @click="$emit('open-sidebar')"
        />
      </div>
    </RouterLink>

    <div class="lists" :class="{ 'close-lists': !sidebarOpen }">
      <RouterLink to="/dashboard" class="list-container">
        <Icon icon="material-symbols:dashboard" width="24" height="24" />
        <div class="link-title">Dashboard</div>
      </RouterLink>
      <RouterLink to="/integrations" class="list-container">
        <Icon icon="mdi:puzzle" width="24" height="24" />
        <div class="link-title">Integrations</div>
      </RouterLink>
      <RouterLink to="/templates" class="list-container">
        <Icon icon="ic:baseline-design-services" width="24" height="24" />
        <div class="link-title">Templates</div>
      </RouterLink>
      <RouterLink to="/workflows" class="list-container">
        <Icon icon="mdi:workflow" width="24" height="24" />
        <div class="link-title">Workflows</div>
      </RouterLink>
      <RouterLink to="/users" class="list-container">
        <Icon icon="mdi:users" width="24" height="24" />
        <div class="link-title">Users</div>
      </RouterLink>
      <RouterLink to="/automation" class="list-container">
        <Icon
          icon="carbon:ibm-cloud-pak-manta-automated-data-lineage"
          width="24"
          height="24"
        />
        <div class="link-title">Automation</div>
      </RouterLink>
      <RouterLink to="/logs" class="list-container">
        <Icon icon="material-symbols-light:data-table" width="24" height="24" />
        <div class="link-title">Logs</div>
      </RouterLink>
    </div>
  </aside>
</template>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@500&display=swap");

.container {
  height: 100vh;
  width: 250px;
  background: #2b2a3d;
  color: white;

  .logo {
    width: 190px;
    height: 65px;
    margin: 0 auto;
    padding-top: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 4px;

    img {
      widows: 41px;
      height: 41px;
    }

    .logo-title {
      font-family: "Poppins", sans-serif;
      font-size: 22px;
      font-weight: 500;
      line-height: 33px;
      letter-spacing: -0.017em;
    }

    .open-sidebar-icon {
      display: none;
    }
  }

  .lists {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 24px;
    padding-left: 33px;
    margin-top: 48px;

    .list-container {
      color: #b0afbb;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .list-container:focus {
      color: white;
    }
  }
}

.close-container {
  width: 60px;
  margin: 0 auto;
  padding: 0;
  position: absolute;
  top: 0;
  left: 0;
  transition: all 0.5s ease-in;

  &:hover {
    width: 250px;

    .open-sidebar-icon {
      display: block;
      margin-left: 8px;
      cursor: pointer;
    }

    .close-lists {
      padding-left: 33px;
    }
  }

  .close-logo {
    width: 100%;

    .logo-title {
      display: none;
    }
  }

  .close-lists {
    align-items: flex-start;
    justify-content: center;
    margin: 0 auto;
    padding: 0 20px;
    margin-top: 48px;

    .link-title {
      display: none;
    }
  }
}

.close-container:hover .logo-title {
  display: flex;
}
.close-container:hover .link-title {
  display: flex;
}
</style>
