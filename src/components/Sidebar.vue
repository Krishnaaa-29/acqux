<script setup>
import { Icon } from "@iconify/vue";
import { RouterLink } from "vue-router";
</script>

<template>
  <aside class="container">
    <RouterLink to="/">
      <div class="logo">
        <img src="../assets/logo.svg" alt="logo" />
        <p>SuprComm</p>
      </div>
    </RouterLink>

    <div class="lists">
      <RouterLink to="/dashboard" class="list-container">
        <Icon icon="material-symbols:dashboard" width="24" height="24" />
        <p>Dashboard</p>
      </RouterLink>
      <RouterLink to="/integrations" class="list-container">
        <Icon icon="mdi:puzzle" width="24" height="24" />
        <p>Integrations</p>
      </RouterLink>
      <RouterLink to="/templates" class="list-container">
        <Icon icon="ic:baseline-design-services" width="24" height="24" />
        <p>Templates</p>
      </RouterLink>
      <RouterLink to="/workflows" class="list-container">
        <Icon icon="mdi:workflow" width="24" height="24" />
        <p>Workflows</p>
      </RouterLink>
      <RouterLink to="/users" class="list-container">
        <Icon icon="mdi:users" width="24" height="24" />
        <p>Users</p>
      </RouterLink>
      <RouterLink to="/automation" class="list-container">
        <Icon
          icon="carbon:ibm-cloud-pak-manta-automated-data-lineage"
          width="24"
          height="24"
        />
        <p>Automation</p>
      </RouterLink>
      <RouterLink to="/logs" class="list-container">
        <Icon icon="material-symbols-light:data-table" width="24" height="24" />
        <p>Logs</p>
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

    p {
      font-family: "Poppins", sans-serif;
      font-size: 22px;
      font-weight: 500;
      line-height: 33px;
      letter-spacing: -0.017em;
    }
  }

  .lists {
    display: flex;
    flex-direction: column;
    align-items: start;
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
</style>
