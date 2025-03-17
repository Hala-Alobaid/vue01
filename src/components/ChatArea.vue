<script setup>
import u1 from '@/assets/u1.png'
import u3 from '@/assets/u3.png'
import ch1 from '@/assets/ch1.png'
import m1 from '@/assets/m1.png'
import m2 from '@/assets/m2.png'
import m3 from '@/assets/m3.png'
import m5 from '@/assets/m5.png'
import m6 from '@/assets/m6.png'
import m7 from '@/assets/m7.png'
import m8 from '@/assets/m8.png'
import m9 from '@/assets/m9.png'
</script>

<script>
export default {
  data() {
    return {
      showBlockModal: false,
      showUnlockModal: false,
      showDeleteModal: false,
      sidebarVisible: window.innerWidth > 1021, 
    };
  },
  methods: {
    toggleSidebar() {
      this.sidebarVisible = !this.sidebarVisible;
    },
    togglemedia() {
      this.showBlockModal = !this.showBlockModal;
      this.showUnlockModal = !this.showUnlockModal;
      this.showDeleteModal = !this.showDeleteModal;
    }
  },
mounted() {
  window.addEventListener("resize", this.handleResize);
},
beforeUnmount() {
  window.removeEventListener("resize", this.handleResize);
},
methods: {
  toggleSidebar() {
    this.sidebarVisible = !this.sidebarVisible;
  },
  handleResize() {
    if (window.innerWidth <= 1021) {
      this.sidebarVisible = false; 
    } else {
      this.sidebarVisible = true;  
    }
  }
}
};
</script>


<template>
    <div class="row d-flex box w-100">
        <div class="col-12 chat-container w-100">
            <header class="d-flex justify-content-between align-items-center bg-white p-3 header1">
                <div class="profile1 d-flex align-items-center me-auto">
                    <img :src="u1" class="rounded-circle" height="40" width="40">
                    <span class="away">Away</span>
                </div>
                <div class="d-flex align-items-center icons">
                  <div>
                    <i class="bi bi-ban ms-5 i1 cursor-pointer" @click="showBlockModal = true"></i>
                    <div v-if="showBlockModal" class="modal-backdrop fade show" @click="showBlockModal = false"></div>
                    <div v-if="showBlockModal" class="modal fade show d-block" tabindex="-1">
                      <div class="modal-dialog modal-dialog-centered">
                        <div class="modal-content text-center p-4">
                          <div class="modal-body">
                            <i class="bi bi-ban i1 d-block mx-auto mb-3"></i>
                            <h5 class="fw-bold">Block User</h5>
                            <p class="text-muted">You Are Going To Block This User, Are You Sure?</p>
                          </div>
                          <div class="modal-footer d-flex justify-content-center border-0">
                            <button class="btn btn-cancel px-4" @click="showBlockModal = false">Cancel</button>
                            <button class="btn btn-yes px-4">Yes</button>
                          </div>
                        </div>
                      </div>
                    </div>
                    <i class="bi bi-unlock ms-4 cursor-pointer" @click="showUnlockModal = true"></i>
                    <div v-if="showUnlockModal" class="modal-backdrop fade show" @click="showUnlockModal = false"></div>
                    <div v-if="showUnlockModal" class="modal fade show d-block" tabindex="-1">
                      <div class="modal-dialog modal-dialog-centered">
                        <div class="modal-content text-center p-4">
                          <div class="modal-body">
                            <i class="bi bi-unlock i1 d-block mx-auto mb-3"></i>
                            <h5 class="fw-bold">Unlock User</h5>
                            <p class="text-muted">You Are Going To Unblock This User, Are You Sure?</p>
                          </div>
                          <div class="modal-footer d-flex justify-content-center border-0">
                            <button class="btn btn-cancel px-4" @click="showUnlockModal = false">Cancel</button>
                            <button class="btn btn-yes px-4">Yes</button>
                          </div>
                        </div>
                      </div>
                    </div>
                    <i class="bi bi-trash3 ms-4 i2 cursor-pointer" @click="showDeleteModal = true"></i>
                    <div v-if="showDeleteModal" class="modal-backdrop fade show" @click="showDeleteModal = false"></div>
                    <div v-if="showDeleteModal" class="modal fade show d-block" tabindex="-1">
                      <div class="modal-dialog modal-dialog-centered">
                        <div class="modal-content text-center p-4">
                          <div class="modal-body">
                            <i class="bi bi-trash3 i1 d-block mx-auto mb-3"></i>
                            <h5 class="fw-bold">Delete Conversation</h5>
                            <p class="text-muted">Once You Sure To Delete This Conversation, You Will Not Be Able To Undo This Action</p>
                          </div>
                          <div class="modal-footer d-flex justify-content-center border-0">
                            <button class="btn btn-cancel px-4" @click="showDeleteModal = false">Cancel</button>
                            <button class="btn btn-yes px-4">Yes</button>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                    <i class="bi bi-telephone ms-4"></i>
                    <i class="bi bi-camera-video ms-3 "></i>
                    <i class="bi bi-list ms-3 me-3 i3"@click="toggleSidebar"></i>
                </div>
            </header>
        <div class="row">
            <div :class="{'col-8': sidebarVisible, 'col-12': !sidebarVisible}" class="view-chat">
                <div class="container chat">
                    <div class="d-flex align-items-center">
                    <img :src="u3" class="u " height="45" width="45">
                    <div class="ms-3">
                      <p class="p1">Andrew, 2hours ago</p>
                    </div>
                    </div>
                      <p class="ms-5 ps-2 p2">If I don't like something, I'll stay away from it.</p>
                </div>
                <div class="d-flex justify-content-end">
                    <div class="ms-3 ">
                    <p class="p3">2hours ago</p>
                    </div>
                </div>
                      <p class="ps-2 pe-3 p4 ">If I don't like something, I'll stay away from it.</p>
                <div class="container chat">
                    <div class="d-flex align-items-center">
                      <img :src="u3" class="u " height="45" width="45">
                    <div class="ms-3">
                      <p class="p1">Andrew, 2hours ago</p>
                    </div>
                    </div>
                      <p class="ms-5 ps-2 p2">I want more detailed information.</p>
                </div>
                <div class="d-flex justify-content-end">
                    <div class="ms-3 ">
                    <p class="p3">2hours ago</p>
                    </div>
                </div>
                    <p class="ps-2 pe-3 p4 ">If I don't like something, I'll stay away from it.</p>
                    <p class="ps-2 pe-3 p5">They got there early, and they got really good seats.</p>
                <div class="container chat">
                    <div class="d-flex align-items-center">
                      <img :src="u3" class="u " height="45" width="45">
                    <div class="ms-3">
                      <p class="p1">Andrew, 2hours ago</p>
                    </div>
                    </div>
                      <img :src="ch1" class="image1 mt-1" height="80" width="104">
                </div>
                <div>
                  <div class="d-flex justify-content-between align-items-center bg-white mt-2  massage">
                    <div class="profile1 d-flex align-items-center me-auto mt-1">
                      <i class="bi bi-emoji-smile ms-2"></i>
                      <p class="massage1">Type a massage</p>
                    </div>
                    <div class="d-flex align-items-center icons">
                      <i class="ic1 bi bi-image"></i>
                      <i class="ic1 bi bi-paperclip"></i>
                      <i class="ic1 bi bi-mic"></i>
                    </div>
                  </div>
                </div>
            </div>
            <div v-show="sidebarVisible" class="col-4 m-sidebar">
              <button class="close-sidebar-btn" @click="sidebarVisible = false">x</button>
                <div class="container">
                  <h6>Media <span class="number">(36)</span></h6>
                  <div class="image2">
                    <img :src="ch1" class="mt-1" height="64" width="68">
                    <img :src="m1" class="mt-1" height="64" width="68">
                    <img :src="m2" class="mt-1" height="64" width="68">
                  </div>
                  <div class="image3">
                    <img :src="m3" class="mt-1" height="64" width="68">
                    <img :src="ch1" class="mt-1" height="64" width="68">
                    <img :src="m1" class="mt-1" height="64" width="68">
                  </div>
                  <h6 class="mt-3">Files <span class="number">(36)</span></h6>
                  <div class="image4">
                    <div class="files-info">
                      <img :src="m5" class="mt-1 ms-0" height="53" width="53">
                      <div class="info mt-1">
                        <h6>service-task.pdf</h6>
                        <p>2MB 2 Dec 2022</p>
                      </div>
                    </div>
                    <div class="files-info">
                      <img :src="m6" class="mt-1 ms-1" height="48" width="48">
                      <div class="info mt-1">
                        <h6>homepage-design.fig</h6>
                        <p>2MB 2 Dec 2022</p>
                      </div>
                    </div>
                    <div class="files-info">
                      <img :src="m7" class="mt-1 ms-1" height="48" width="48">
                      <div class="info mt-1">
                        <h6>about-us.html</h6>
                        <p>2MB 2 Dec 2022</p>
                      </div>
                    </div>
                    <div class="files-info">
                      <img :src="m8" class="mt-1 ms-1" height="50" width="46">
                      <div class="info mt-1">
                        <h6>work-project.zip</h6>
                        <p>2MB 2 Dec 2022</p>
                      </div>
                    </div>
                    <div class="files-info">
                      <img :src="m9" class="mt-1 ms-1" height="48" width="48">
                      <div class="info mt-1">
                        <h6>custom.js</h6>
                        <p>2MB 2 Dec 2022</p>
                      </div>
                    </div>
                  </div>
                </div>
            </div>
        </div>
        </div>
    </div>
</template>

<style>
.profile1 {
  display: flex;
  align-items: center;
  gap: 10px;
}
.header1{
  max-width: 100%;
  position: relative; 
}
.header1::before {
  content: "";
  position: absolute;
  bottom: 0;
  width: 60vw;
  left: 0;
  height: 1px;
  background-color: #ddd;
}
.away {
  color: rgb(152, 164, 174); 
  font-size: 14px; 
}
.i1{
  color: rgb(99, 91, 255);
}
.i2{
  color:rgb(255, 0, 0)
}
.i3 {
  font-size: 25px;
  color: black ;
}
.media-dropdown {
  position: relative;
  top: 100%;
  background: white;
  border: 1px solid #ddd;
  padding: 5px;
  border-radius: 5px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
}
.view-chat {
  background: white; 
  padding: 10px;
  height: 84vh;
}
.m-sidebar {
  background: white;
  padding: 15px;
  height: 84vh;
  overflow-y: auto;
  position: relative;
  border-left: none; 
}
.m-sidebar::before {
  content: "";
  position: absolute;
  left: 0;
  top: 0; 
  height: 100%; 
  width: 0.5px;
  background: #ddd;
}
.p1 {
  color: rgb(152, 164, 174); 
  font-size: 14px;
  margin: 0;
}
.p2 {
  display: inline-block;
  border: 1px solid rgb(239, 244, 250);
  padding: 4px;
  border-radius: 6px;
  background-color: rgb(239, 244, 250);
}
.p3{
  color: rgb(152, 164, 174); 
  font-size: 14px;
  margin: 0;
}
.p4{
  text-align: right; 
  margin-left: auto;
  margin-right: 0;
  margin-left: 150px;
  border: 1px solid rgb(236, 253, 253);
  padding: 4px;
  border-radius: 6px;
  background-color: rgb(236, 253, 253);
}
.p5{
  text-align: right; 
  margin-left: auto;
  margin-right: 0;
  margin-left: 110px;
  border: 1px solid rgb(236, 253, 253);
  padding: 4px;
  border-radius: 6px;
  background-color: rgb(236, 253, 253);
}
.image1{
  margin-left: 61px;
}
.massage{
  position: relative; 
}
.massage::before {
  content: "";
  position: absolute;
  top: 0;
  width: 37.2vw;
  height: 1px;
  background-color: #ddd;
}
.massage1{
  color: rgb(152, 164, 174); 
  font-size: 14px;
  border-radius: none;
  margin: 0;
  padding: 0;
}
.ic1{
  margin-left: 15px;
  padding: 0;
}
.number{
  color:rgb(152, 164, 174)
}
.image2, .image3 {
  display: flex;
  gap: 10px;
}
.image2 img, .image3 img {
  border-radius: 15px;
  object-fit: cover;   
}
.image4{
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.image4 img{
  object-fit: cover;
}
.files-info{
  display: flex;
  align-items: center; 
  gap: 5px;
  font-size: 1pc;
}
.info {
  display: flex;
  flex-direction: column; 
  justify-content: center;
  margin: 0;
  padding: 0;
  height: 45px;
  line-height: 1.2; 
}
.info h6{
  font-size: 16px;
  margin: 0;
}
.info p{
  font-size: 12px;
  color: gray;
  margin: 3px;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(83, 83, 83, 0.323) !important;
  z-index: 1040;
}
.cursor-pointer {
  cursor: pointer;
}
.btn-yes {
  background-color: rgb(87, 92, 212) !important; 
  color: rgb(255, 255, 255) !important;
  border: none;
}
.btn-cancel {
  background-color: rgb(149, 149, 149) !important; 
  color: white !important;
  border: none;
}
.btn-yes:hover {
  filter: brightness(1.2);
}
.btn-cancel:hover {
  filter: brightness(1.2);
}

@media (max-width: 1021px) {
  .icons i {
    font-size: 18px;
    margin: 0 5px;
  }
  .profile1 img {
    width: 30px;
    height: 30px;
  }
}
@media (max-width: 1021px) {
  .row {
    flex-direction: column;
  }

  .view-chat {
    width: 100%;
    height: 41vh;
    overflow-y: auto;
  }

  .m-sidebar {
    position: fixed;
    bottom: 0;
    right: 150px; 
    width: 100%;
    background: white;
    padding: 15px;
    height: 50vh;
    z-index: 999;
    border-left: none;
    border-top: none;
    box-shadow: 0 -2px 5px rgba(0, 0, 0, 0.2);
    overflow-y: auto; 
  }

  .image2, .image3 {
    display: flex;
    gap: 5px; 
  }

  .image2 img, .image3 img {
    border-radius: 15px;
    object-fit: cover;
    width: 50px; 
    height: 50px; 
  }

  .image4 {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .image4 img {
    object-fit: cover;
    width: 50px; 
    height: 50px; 
  }

  .files-info {
    display: flex;
    align-items: center;
    gap: 5px;
    font-size: 1rem;
  }

  .info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0;
    padding: 0;
    height: 50px; 
    line-height: 1.2;
  }

  .info h6 {
    font-size: 10px;
    margin: 0;
  }

  .info p {
    font-size: 7px;
    color: gray;
    margin: 3px;
  }

  .icons i {
    font-size: 15px; 
    margin: 0 5px;
  }

  .profile1 img {
    width: 30px;
    height: 30px;
  }

  .massage {
    position: relative;
  }

  .massage::before {
    content: "";
    position: absolute;
    top: 0;
    width: 37.2vw;
    height: 1px;
    background-color: #ddd;
  }

  .massage1 {
    color: rgb(152, 164, 174);
    font-size: 14px;
    border-radius: none;
    margin: 0;
    padding: 0;
  }
}

.close-sidebar-btn {
  position: absolute;
  top: 5px;
  right: 10px;
  background-color: rgb(99, 91, 255);
  color: white;
  border: none;
  padding: 6px;
  cursor: pointer;
  font-size: 16px;
  border-radius: 5px;
  display: block;
}

@media (min-width: 1025px) {
  .close-sidebar-btn {
    display: none;
  }
}
</style>
