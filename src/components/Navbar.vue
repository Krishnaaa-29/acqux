<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps({
  sidebarOpen: {
    type: Boolean,
    required: true,
  },
});

defineEmits(["toggle-sidebar"]);
</script>

<template>
  <nav :class="{ 'full-navbar': !sidebarOpen }">
    <div class="left-nav">
      <Icon
        icon="heroicons-solid:menu-alt-2"
        width="32"
        height="32"
        @click="$emit('toggle-sidebar')"
        class="toggle-btn"
      />
      <div class="search-field">
        <input type="text" placeholder="Search here" />
        <div class="button">
          <button>Search</button>
          <Icon icon="bitcoin-icons:search-outline" width="20" height="20" />
        </div>
      </div>
    </div>
    <div class="right-nav">
      <Icon icon="uiw:mail-o" width="32" height="32" />
      <Icon icon="system-uicons:bell" width="32" height="32" />
      <div class="profile">
        <div class="profile-pic"></div>
        <div class="content">
          <h1>Rohan Joshi</h1>
          <p>Admin</p>
        </div>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
nav {
  width: calc(100vw - 298px);
  /* min-width: 320px; */
  background: #ffffff;
  height: 70px;
  margin: 0 auto;
  padding: 0 24px;
  margin-top: 24px;
  color: #a2a1b9;

  display: flex;
  align-items: center;
  justify-content: space-between;

  .left-nav {
    display: flex;
    align-items: center;
    gap: 24px;

    .toggle-btn {
      cursor: pointer;
    }
    .search-field {
      display: flex;

      input {
        background: #f2f1f8;
        height: 40px;
        width: 164px;
        padding: 0 8px;

        font-family: "Poppins";
        font-size: 14px;
        font-weight: 400;
        line-height: 18px;
        letter-spacing: -0.017em;
      }

      .button {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 4px;
        background: #6460e8;
        height: 40px;
        width: 98px;
        color: #ffffff;
        padding: 8px;

        font-size: 14px;
      }
    }
  }

  .right-nav {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 24px;

    .profile {
      display: flex;
      align-items: center;
      gap: 12px;
      .profile-pic {
        height: 40px;
        width: 40px;
        background: #6460e8;
      }

      .content {
        h1 {
          font-family: Poppins;
          color: #000;
          font-size: 18px;
          font-weight: 600;
          line-height: 27px;
          letter-spacing: -0.017em;
        }

        p {
          font-family: Poppins;
          font-size: 14px;
          font-weight: 400;
          line-height: 21px;
          letter-spacing: -0.017em;
        }
      }
    }
  }
}
.full-navbar {
  width: calc(100vw - 108px);
  margin-left: 84px;
  transition: all 0.5s ease-in;
}
</style>
