<template>
  <div class="header">
    <ul class="menu">
      <li v-for="(item, index) in menuItems" :key="index" class="menu-item">
        <a @mouseover="openDrawer(index)" @mouseout="closeDrawer(index)">{{
          item
        }}</a>
        <div class="drawer" :class="{ open: isDrawerOpen[index] }">
          <div class="drawer-content">
            <p>{{ item }} content</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuItems: ["Mac", "iPad", "iPhone", "Watch", "TV", "Music", "Support"],
      isDrawerOpen: Array(7).fill(false),
    };
  },
  methods: {
    openDrawer(index) {
      this.isDrawerOpen.splice(index, 1, true);
      document.body.classList.add("blur");
    },
    closeDrawer(index) {
      this.isDrawerOpen.splice(index, 1, false);
      document.body.classList.remove("blur");
    },
  },
};
</script>

<style scoped>
.header {
  padding: 20px;
  position: relative;
  z-index: 2;
}

.menu {
  display: flex;
  justify-content: space-between;
  list-style: none;
  padding: 5px;
}

.menu-item {
  position: relative;
  margin: 20px;
  cursor: pointer;
}

.menu-item a {
  color: #000;
  text-decoration: none;
  font-weight: bold;
}

.drawer {
  position: absolute;
  top: calc(100% + 10px);
  left: 0;
  width: 200px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  opacity: 0;
  visibility: hidden;
  transform: translateY(-10px);
  transition: opacity 0.5s, visibility 0s linear 0.3s, transform 0.5s;
  z-index: 1;
}

.drawer.open {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
  transition-delay: 0s, 0s, 0s;
}

.drawer-content {
  margin-top: 10px;
}

body.blur {
  filter: blur(5px);
}
</style>