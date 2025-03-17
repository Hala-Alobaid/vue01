<script setup>
import u0 from '@/assets/u0.png'
</script>

<script>
import u1 from '@/assets/u1.png'
import u2 from '@/assets/u2.png'
import u3 from '@/assets/u3.png'
import u4 from '@/assets/u4.png'
import u5 from '@/assets/u5.png'
export default {
  data() {
    return {
      search: "",
      chats: [
         {
          id: 0,
          name: 'Mathew Anderson',
          message: 'Marketing Director',
          time: '',
          avatar: u0, 
          status: 'online',
          active: false, 
        },
        {
          id: 1,
          name: 'Michell Flintoff',
          message: 'You: Yesterday was great...',
          time: '15 minutes',
          avatar: u1, 
          status: 'online',
          active: false,
        },
        {
          id: 2,
          name: 'Bianca Anderson',
          message: 'Nice looking dress you...',
          time: '30 minutes',
          avatar: u2,
          status: 'offline',
          active: false,
          unread: 0,
        },
        {
          id: 3,
          name: 'Andrew Johnson',
          message: 'Sent a photo',
          time: '2 hours',
          avatar: u3,
          status: 'waiting',
          active: false,
        },
        {
          id: 4,
          name: 'Mark Strokes',
          message: 'Lorem ipsum text sud...',
          time: '5 days',
          avatar: u4,
          status: 'online',
          active: false,
        },
        {
          id: 5,
          name: 'Mark, Stoinus & Rish...',
          message: 'Lorem ipsum text...',
          time: '5 days',
          avatar: u5,
          status: 'online',
          active: false,
        },
        {
          id: 6,
          name: 'Bainca Anderson',
          message: 'Nice looking dress you...',
          time: '30 minutes',
          avatar: u2,
          status: 'offline',
          active: false,
          unread: 0,
        },
      ],
      statusColors: {
        online: "bg-green-500",
        offline: "bg-red-500",
        waiting: "bg-yellow-500",
      },
    };
  },
  computed: {
  filteredChats() {
    return this.chats.filter(chat =>
      chat.name.toLowerCase().includes(this.search.toLowerCase()) &&
      chat.id !== 0
    );
  }
},
  methods: {
    setActive(selectedId) {
      this.chats.forEach(chat => chat.active = chat.id === selectedId);
    }
}
};
</script>



<template>
  <div class="sidebar chat-sidebar">
    <div class="d-md-block bg-white profile ms-1 mt-3">
      <div class="profile-info chat-item "> 
        <div class="avatar-wrapper">
          <img :src="u0" class="avatar" height="45" width="45" />
          <span class="status-indicator online"></span>
        </div>
        <div class="chat-info">
          <div class="chat-header">
            <h4>Mathew Anderson</h4>
          </div>
          <p class="message">Marketing Director</p>
        </div>
        <i class="bi bi-three-dots-vertical"></i>
      </div>
      <div class="search-bar mt-3">
        <input v-model="search" type="text" placeholder="Search Contacts" class="px-3 py-1 fs-6 rounded border w-100" />
        <i class="bi bi-search" v-if="!search"></i>
      </div>
      <div class="recent-chats mt-5 mb-2 ms-3">
        <div class="custom-select-wrapper">
          <select class="custom-select">
            <option selected>Recent Chats</option>
            <option value="1">Sort by time</option>
            <option value="2">Sort by unread</option>
            <option value="3">Mark all as read</option>
          </select>
          <i class="bi bi-chevron-down ic5"></i>
        </div>
      </div>
      <div class="chat-list">
        <div
          v-for="chat in filteredChats"
          :key="chat.id"
          :class="['chat-item', { active: chat.active }]"
          @click="setActive(chat.id)"
        >
          <div class="avatar-wrapper">
            <img :src="chat.avatar" alt="avatar" class="avatar" />
            <span :class="['status-indicator', chat.status]"></span>
          </div>
          <div class="chat-info">
            <div class="chat-header">
              <h4>{{ chat.name }}</h4>
              <span class="time">{{ chat.time }}</span>
            </div>
            <p class="message">{{ chat.message }}</p>
          </div>
          <div v-if="chat.unread > 0" class="unread-badge">
            {{ chat.unread }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<style>
.chat-sidebar {
  width: 100%;
  height: 75vh !important;
  background: #ffffff;
  padding: 20px;
  border-radius: 10px 0 0 10px;
  font-family: Arial, sans-serif; 
}
.profile {
  display: flex;
  align-items: center;
  gap: 10px;
  position: relative;
  border-left: none;
  height: 636px;
}
.profile::before {
  content: "";
  position: absolute;
  right: 0; 
  top: -21px;
  height: 200%; 
  width: 1px; 
  background: #ddd; 
}
.profile-info {
  display: flex;
  align-items: center; 
  gap: 10px; 
}
.u {
  width: 45px;
  height: 45x;
  border-radius: 50%;
  border: 2px solid #e0e0e0;
}
.user {
  display: flex;
  flex-direction: column; 
  justify-content: center;
  margin: 0;
  padding: 0;
  height: 45px;
  line-height: 1.2; 
}
.user h3 {
  font-size: 16px;
  margin: 0;
}
.user p {
  font-size: 12px;
  color: gray;
  margin: 3px;
}
.search-bar {
  position: relative;
  width: 100%;
  max-width: 100px; 
  min-width: 275px;
  margin-left: 15px;
}
.search-bar input {
  width: 100%;
  padding-left: 35px !important; 
  border-radius: 8px;
  border: 1px solid #e0e0e0;
  outline: none;
}
.search-bar i {
  position: absolute;
  left: -30px; 
  top: 50%;
  transform: translateY(-50%);
  color: #888; 
  font-size: 16px;
}
.search-bar input::placeholder {
  color: gray;
}
.custom-select {
  background: none; 
  border: none; 
  color: #888;
  font-size: 14px;
  cursor: pointer;
  outline: none; 
  appearance: none; 
  padding-right: 23px; 
}
.custom-select-wrapper {
  position: relative;
  display: inline-block;
}
.custom-select-wrapper .ic5 {
  position: absolute;
  right: 5px; 
  top: 50%;
  transform: translateY(-50%);
  font-size: 14px;
  color: #888; 
  pointer-events: none; 
}
.bi{
  cursor: pointer;
  margin-left: 40px; 
  font-size: 20px; 
}
.chat-list {
  width: 300px;
  border:none;
  overflow: hidden;
  background: #fff;
}
.chat-item {
  display: flex;
  align-items: center;
  padding: 10px;
}
.chat-item:hover {
  background-color: rgb(246, 247, 249);
}
.chat-item.active {
  background-color: #e0f7fa;
}
.avatar-wrapper {
  position: relative;
  margin-right: 12px;
}
.chat-item:last-child {
  border-bottom: none;
}
.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin-right: 10px;
}
.status-indicator {
  position: absolute;
  bottom: 0;
  right: 0;
  left: 30px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: 2px solid #fff;
}
.status-indicator.online {
  background-color: rgb(54, 199, 108); 
}

.status-indicator.offline {
  background-color: rgb(255, 102, 146); 
}
.status-indicator.waiting {
  background-color: rgb(255, 214, 72); 
}
.chat-info {
  flex: 1;
}
.chat-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.chat-header h4 {
  margin: 0;
  font-size: 16px;
}
.time {
  font-size: 12px;
  color: #999;
}
.message {
  margin: 5px 0 0;
  color: rgb(152, 164, 174);
  font-size: 12px;
}
.unread-badge {
  background-color: #ff0000d2;
  color: #fff;
  font-size: 9px;
  padding: 4px 8px;
  border-radius: 12px;
  font-weight: bold;
  margin-top: 10px;
}
.chat-item.active{
  background-color: rgb(237, 237, 238);
}
@media (max-width: 1021px) {
  .chat-sidebar {
    height: 100vh; 
    max-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .profile {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 10px;
    width: 100%;
    height: 47vh !important;
  }

  .profile-info {
    text-align: center;
    width: 100%;
  }

  .search-bar {
    width: 90%;
    margin: 10px auto;
    text-align: center;
  }

  .search-bar input {
    width: 100%;
    padding: 8px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }

  .chat-list {
    width: 100%;
    max-height: 70vh;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    padding: 0 10px;
  }

  .chat-item {
    display: flex;
    align-items: center;
    padding: 10px;
    width: 100%;
    border-bottom: 1px solid #eee;
    position: relative;
  }

  .chat-item .avatar-wrapper {
    margin-right: 10px;
  }

  .chat-info {
    flex-grow: 1;
    text-align: left;
  }

  .chat-info .name {
    font-weight: bold;
  }

  .chat-info .last-message {
    color: gray;
    font-size: 14px;
  }

  .chat-item .notification-badge {
    background-color: red;
    color: white;
    font-size: 12px;
    padding: 4px 8px;
    border-radius: 50%;
    position: absolute;
    right: 10px;
  }
}

</style>