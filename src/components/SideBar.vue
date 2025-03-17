<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import logo from '@/assets/logo.png';

const isSidebarOpen = ref(false);
const isMobile = ref(window.innerWidth <= 1021);
const showPermissions = ref(false);

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};

const closeSidebar = () => {
  isSidebarOpen.value = false;
};

const checkScreenSize = () => {
  isMobile.value = window.innerWidth <= 1021;
  if (!isMobile.value) {
    isSidebarOpen.value = false;
  }
};

const togglePermissions = () => {
  showPermissions.value = !showPermissions.value;
};

onMounted(() => {
  window.addEventListener("resize", checkScreenSize);
});

onUnmounted(() => {
  window.removeEventListener("resize", checkScreenSize);
});
</script>


<template>
  <button v-if="isMobile && !isSidebarOpen" class="menu-btn" @click="toggleSidebar">
    <i class="bi bi-list"></i> 
  </button>
  <div :class="['sidebar1', { 'sidebar-open': isSidebarOpen }]">
    <nav class="d-md-block bg-white hv-100">
      <button v-if="isMobile" class="close-btn" @click="closeSidebar">
        <i class="bi bi-x"></i>
      </button>
      <div class="d-flex align-items-center px-1">
        <img :src="logo" class="logo me-2" alt="logo">
        <h5>Hi TEAM</h5>
      </div>           
      <ul class="nav flex-column px-2 mt-3">
        <li class="nav-item p-2"><i class="bi bi-house-door"></i>Dashboard</li>
        <li class="nav-item p-2"><i class="bi bi-box"></i>Orders</li>
        <li class="nav-item p-2"><i class="bi bi-people"></i>Passengers</li> 
        <li class="nav-item p-2"><i class="bi bi-truck-front"></i>Captains</li>
        <li class="nav-item p-2"><i class="bi bi-clipboard-minus"></i>Categories</li>
        <hr class="custom-hr m-1" />
        <li class="nav-item p-2"><i class="bi bi-file-text"></i>Settlement</li>
        <hr class="custom-hr m-1" />
        <li class="nav-item p-2"><i class="bi bi-chat-left"></i>Contact</li>
        <li class="nav-item p-2"><i class="bi bi-stars"></i>Reviews</li>
        <hr class="custom-hr m-1" />
        <li class="nav-item p-2 dropdown" @click="togglePermissions">
          <i class="bi bi-shield-shaded"></i> Permissions 
          <i class="bi bi-chevron-down ms-4"></i>
        </li>
        <ul v-show="showPermissions" class="submenu">
          <li class="nav-item p-2 ps-4"><i class="bi bi-person"></i> Users</li>
          <li class="nav-item p-2 ps-4"><i class="bi bi-key"></i> Roles</li>
          <li class="nav-item p-2 ps-4"><i class="bi bi-lock"></i> Access</li>
        </ul>
        <li class="nav-item p-2"><i class="bi bi-globe2"></i>Translation</li>
        <li class="nav-item p-2"><i class="bi bi-film"></i>Education Video</li>
        <li class="nav-item p-2"><i class="bi bi-gear"></i>Settings</li>
        <li class="nav-item p-2"><i class="bi bi-square"></i>Content</li>
      </ul>
    </nav>
  </div>
  <div v-if="isSidebarOpen" class="overlay show" @click="closeSidebar"></div>
</template>


<style>
.logo {
  width: 50px;
  height: 50px;
  border-radius: 50%; 
}
.mw{
  max-width: 250px;
}
.nav-item i {
  font-size: 18px;
  margin-right: 10px;
  margin-left: 2px; 
  color: rgb(152, 164, 174);
}
.nav-item {
  color: #000000;
  font-weight: 450;
}
.nav-item:hover {
  background-color: rgb(99, 91, 255); 
  color: rgb(255, 255, 255); 
  border-radius: 10px;
}
.nav-item:hover i {
  color: rgb(255, 255, 255);
}
.submenu {
  list-style: none;
  padding-left: 10px;
}
.dropdown {
  cursor: pointer; 
}
nav {
    height: 60vh;
}
@media (max-width:  1021px) {
  .sidebar1 {
    position: fixed;
    top: 0;
    left: -250px; 
    width: 250px;
    height: 100vh;
    background: white;
    transition: left 0.3s ease-in-out;
    z-index: 1000;
  }

  .sidebar-open {
    left: 0 !important; 
  }

  .menu-btn {
  position: fixed;
  top: 10px;
  left: 10px;
  background: #ffffff;
  border: 1px solid rgba(0, 0, 0, 0.295);
  border-radius: 50%;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.312);
  width: 33px;
  height: 33px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 1100;
  transition: all 0.3s ease-in-out;
  }

  .menu-btn i {
  font-size: 22px;
  color: rgb(0, 0, 0);
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  }
  .menu-btn:hover {
  border-color: rgb(255, 255, 255); 
  background-color: rgba(62, 62, 62, 0.305);
  }
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.5);
    display: none;
    z-index: 999;
  }

  .overlay.show {
    display: block; 
  }
}
.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  z-index: 1101;
}

.close-btn i {
  color: rgb(0, 0, 0);
}

.close-btn:hover i {
  color: rgb(0, 0, 0);
}
</style>   
