<template>
  <q-layout view="hHh Lpr fFf">
    <!-- Header -->
    <q-header elevated>
      <q-toolbar>
        <div class="header-icons">
          <q-btn dense flat round @click="toggleDrawer" icon="menu" />
          <img
            src="../assets/youtube.png"
            class="youtube-icon"
            width="88"
            alt=""
            srcset=""
          />
        </div>

        <div class="header-icons">
          <q-input
            rounded
            outlined
            color="grey-3"
            placeholder="Search videos"
            class="search-input"
          >
            <template v-slot:append>
              <q-icon name="search" class="icon" />
            </template>
          </q-input>
          <q-icon name="mic" class="icon" />
        </div>

        <div class="header-icons">
          <q-icon name="settings" class="icon" />
          <q-avatar class="avatar" size="sm">
            <img src="https://via.placeholder.com/40" alt="User Avatar" />
          </q-avatar>
        </div>
      </q-toolbar>
    </q-header>

    <!-- Drawer (Menu) -->
    <q-drawer
      v-model="drawer"
      show-if-above
      :width="drawerWidth"
      :content-class="$q.dark.isActive ? 'bg-dark' : ''"
      side="left"
    >
      <q-list>
        <q-item clickable v-for="(item, index) in menuItems" :key="index">
          <q-item-section>
            <q-item-label>
              <q-icon :name="item.icon" class="item-icon" />
              <span v-show="drawer">{{ item.label }}</span>
            </q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <!-- Page Contents -->
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      drawerWidth: 250,
      menuItems: [
        { label: "Home", icon: "home" },
        { label: "Trending", icon: "trending_up" },
        { label: "Subscriptions", icon: "subscriptions" },
        { label: "Library", icon: "video_library" },
        { label: "History", icon: "history" },
      ],
      showSearch: false,
      searchQuery: "",
    };
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer;
    },
    toggleSearch() {
      this.showSearch = !this.showSearch;
      if (!this.showSearch) {
        this.searchQuery = "";
      }
    },
  },
};
</script>

<style>
.row {
  gap: 20rem;
}
.q-toolbar {
  min-height: 87px;
}
.youtube-icon {
  margin-right: 7rem;
}
.q-layout__section--marginal {
  background-color: white !important;
  color: black !important;
}
.header-icons {
  display: flex;
  align-items: center;
}
.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.icon {
  margin: 0 10px;
  cursor: pointer;
}

.avatar {
  margin-left: auto;
}

.item-icon {
  margin-right: 10px;
}

.search-input {
  width: 750px; /* Adjust width as needed */
}
</style>
