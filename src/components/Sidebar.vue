<script setup>
import { Icon } from "@iconify/vue";
import { RouterLink } from "vue-router";
import { reactive } from "vue";

const logState = reactive({
  isLogs: false,
});

const workflowState = reactive({
  isWorkflow: false,
});

const toggleLogs = () => {
  logState.isLogs = !logState.isLogs;
};

const toggleWorkflows = () => {
  workflowState.isWorkflow = !workflowState.isWorkflow;
};

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

    <ul class="lists" :class="{ 'close-lists': !sidebarOpen }">
      <RouterLink to="/dashboard" class="list-container">
        <Icon icon="material-symbols:dashboard" width="24" height="24" />
        <p class="link-title">Dashboard</p>
      </RouterLink>
      <RouterLink to="/integrations" class="list-container">
        <Icon icon="mdi:puzzle" width="24" height="24" />
        <p class="link-title">Integrations</p>
      </RouterLink>
      <RouterLink to="/templates" class="list-container">
        <Icon icon="ic:baseline-design-services" width="24" height="24" />
        <p class="link-title">Templates</p>
      </RouterLink>
      <div class="list-container" @click="toggleWorkflows">
        <Icon icon="mdi:workflow" width="24" height="24" />
        <p class="link-title">Workflows</p>
        <Icon
          v-if="workflowState.isWorkflow"
          icon="carbon:chevron-up"
          width="20"
          height="20"
        />
        <Icon v-else icon="carbon:chevron-down" width="20" height="20" />
      </div>
      <RouterLink
        to="/workflows/events"
        v-if="workflowState.isWorkflow"
        class="list-container"
      >
        <Icon icon="fluent-mdl2:radio-bullet" width="20" height="20" />
        <p class="link-title">Events</p>
      </RouterLink>
      <RouterLink
        to="/workflows/route"
        v-if="workflowState.isWorkflow"
        class="list-container"
      >
        <Icon icon="fluent-mdl2:radio-bullet" width="20" height="20" />
        <p class="link-title">Route</p>
      </RouterLink>
      <RouterLink to="/users" class="list-container">
        <Icon icon="mdi:users" width="24" height="24" />
        <p class="link-title">Users</p>
      </RouterLink>
      <RouterLink to="/automation" class="list-container">
        <Icon
          icon="carbon:ibm-cloud-pak-manta-automated-data-lineage"
          width="24"
          height="24"
        />
        <p class="link-title">Automation</p>
      </RouterLink>
      <div class="list-container" @click="toggleLogs">
        <Icon icon="material-symbols-light:data-table" width="24" height="24" />
        <p class="link-title">Logs</p>
        <Icon
          v-if="logState.isLogs"
          icon="carbon:chevron-up"
          width="20"
          height="20"
        />
        <Icon v-else icon="carbon:chevron-down" width="20" height="20" />
      </div>
      <RouterLink to="/logs/sent" v-if="logState.isLogs" class="list-container">
        <Icon icon="fluent-mdl2:radio-bullet" width="20" height="20" />
        <p class="link-title">Sent</p>
      </RouterLink>
      <RouterLink
        to="/logs/automation"
        v-if="logState.isLogs"
        class="list-container"
      >
        <Icon icon="fluent-mdl2:radio-bullet" width="20" height="20" />
        <p class="link-title">Automation</p>
      </RouterLink>
      <RouterLink
        to="/logs/recieved"
        v-if="logState.isLogs"
        class="list-container"
      >
        <Icon icon="fluent-mdl2:radio-bullet" width="20" height="20" />
        <p class="link-title">Recieved</p>
      </RouterLink>
    </ul>
  </aside>
</template>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@500&display=swap");

.container {
  height: 100vh;
  width: 250px;
  background: #2b2a3d;
  color: white;
  transition: 0.5s;
  overflow: hidden;

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
      width: 100%;
      color: #b0afbb;
      display: flex;
      align-items: center;
      justify-content: flex-start;
      gap: 20px;
      cursor: pointer;

      .link-title {
        width: 120px;
      }
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
  position: fixed;
  top: 0;
  left: 0;
  overflow: hidden;

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

    .list-container {
      width: auto;
    }
  }
}

.close-container:hover .logo-title {
  display: flex;
}
</style>
