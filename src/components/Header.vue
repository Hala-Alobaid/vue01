<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import flag1 from '@/assets/flag.png';
import flag2 from '@/assets/flag2.png';
import flag3 from '@/assets/flag3.png';
import u0 from '@/assets/u0.png';

const showPr1 = ref(false);
const showFlagsDropdown = ref(false);
const selectedFlag = ref(flag1);

const flags = [
  { name: 'English', src: flag1 },
  { name: 'Arabic', src: flag2 },
  { name: 'French', src: flag3 }
];

const togglePr1 = () => {
  showPr1.value = !showPr1.value;
};

const toggleFlagsDropdown = () => {
  showFlagsDropdown.value = !showFlagsDropdown.value;
};

const selectFlag = (flag) => {
  selectedFlag.value = flag.src;
  showFlagsDropdown.value = false; 
};

const closeMenu = (event) => {
  if (!event.target.closest('.dropdown')) {
    showPr1.value = false;
  }
};

onMounted(() => {
  document.addEventListener('click', closeMenu);
});
onUnmounted(() => {
  document.removeEventListener('click', closeMenu);
});
</script>


<template>
    <header class="d-flex w-100 justify-content-between align-items-center p-4 bg-white header">
        <div class="d-flex align-items-center">
            <i class="bi bi-search me-3"></i>
            <i class="bi bi-grid"></i>
        </div>
        <div class="d-flex align-items-center">
            <i class="bi bi-moon me-0"></i>
            <i class="bi bi-bell me-3"></i>
            <div class="d-flex position-relative flag-dropdown">
              <img :src="selectedFlag" class="flag1 me-2" alt="flag" width="25" @click="toggleFlagsDropdown">
              <ul v-show="showFlagsDropdown" class="menu position-absolute bg-white shadow rounded">
                <li v-for="flag in flags" :key="flag.name" @click="selectFlag(flag)">
                  <img :src="flag.src" :alt="flag.name" width="25" class="me-2"> {{ flag.name }}
                </li>
              </ul>
            </div>
            <div class="d-flex position-relative">
                <li class="nav-item p-1 dropdown d-flex align-items-center" @click="togglePr1">
                    <img :src="u0" class="pr1" alt="pr1" width="33">
                    <i class="bi bi-chevron-down ms-2"></i>
                </li>
                <ul v-show="showPr1" class="menu position-absolute bg-white shadow rounded">
                    <button class="b1">
                        <i class="bi bi-person"></i> Your Profile
                    </button>
                    <button class="b1">
                        <i class="bi bi-box-arrow-right"></i> Sign Out
                    </button>
                </ul>
            </div>
        </div>
    </header>
</template>

<style>
.header {
  width: 100%;
  height: 8%;
  background-color: #ffffff;
  position: relative;
  z-index: 10;
}
.pr1 {
  border-radius: 50%;
}
.menu {
  list-style: none;
  min-width: 180px;
  position: absolute;
  top: 100%;
  right: 0; 
  z-index: 1000;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  padding: 0;
  background: white;
  overflow: hidden; 
  margin-top: 8px; 
}
.b1 {
  all: unset;
  display: block;
  width: 100%; 
  text-align: left; 
  cursor: pointer;
  padding: 10px 12px;
  padding-left: 0.500%;
}
.b1:hover {
  background-color: rgb(99, 91, 255);
  color: #ffffff;
  border-radius: 6px;
  width: 93%;
}
.menu li {
  cursor: pointer;
  padding: 8px;
  display: flex;
  align-items: center;
}
.menu li:hover {
  background-color: rgb(99, 91, 255);
  color: #ffffff;
}
.flag-dropdown {
  cursor: pointer;
}

</style>
