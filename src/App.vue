<script setup>
import SideBar from './components/SideBar.vue'
import Header from './components/Header.vue'
import ChatTitle from './components/ChatTitle.vue' 
import User from './components/User.vue'
import ChatArea from './components/ChatArea.vue'
</script>

<template>
  <div class="Sidebar-container">
    <div class="sidebar">
      <SideBar />
    </div>
    <div class="header1">
      <Header />
      <div class="chat-wrapper">
        <div class="chat-container">
          <ChatTitle />
        </div>
        <div class="chat-area-container">
          <div class="User">
            <User />
          </div>
          <div class="chat-area">
            <ChatArea />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.Sidebar-container {
  display: grid;
  grid-template-columns: 250px auto; 
  min-height: 100vh;
  height: 100vh;
  background: rgb(244, 247, 251);
  overflow: auto;
}
.sidebar {
  background: #ffffff;
  padding: 5px;
  height: 130vh;
}
.header1 {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.chat-wrapper {
  display: grid;
  grid-template-rows: auto 1fr;
  gap: 20px;
  padding: 0.5rem; 
  max-width: 100%; 
  margin: auto; 
}
.chat-container {
  background: #ffffff;
  border-radius: 15px;
  width: 100%;
  height: 60px;
  overflow: hidden;
}
.chat-area-container {
  display: grid;
  grid-template-columns: 320px auto;
  margin-right: 100px;
  gap: 0;
  width: 100%;
  height: 94.5vh;
}
.User {
  background: #ffffff;
  border-radius: 10px 0 0 10px;
  min-width: 200px;
  overflow: hidden;
}
.chat-area {
  background: #ffffff;
  border-radius: 0 10px 10px 0;
  overflow: hidden;
}
@media (max-width: 1024px) {
  .Sidebar-container {
    grid-template-columns: 1fr;
  }
  .sidebar {
    height: auto;
  }
  .chat-area-container {
    grid-template-columns: 1fr; 
  }
  .User {
    border-radius: 10px;
  }
  .chat-area {
    border-radius: 10px;
  }
}
</style>
