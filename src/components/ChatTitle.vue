<template>
    <nav class="navbar nav1">
        <div class="container-fluid d-flex justify-content-between align-items-center">
            <span class="navbar-brand">Chat</span>
        <div class="nav-icons d-flex align-items-center">
            <i class="bi bi-house icon me-2"></i>
            <i class="bi bi-slash-lg me-2"></i>
            <button class=" botton1">Chat</button>
        </div>
        </div>
    </nav>

</template>


<style>
.nav1 {
    width: 100%; 
    height: 60px;
    margin: auto;  
    background-color: rgb(255, 255, 255);
    padding: 0 15px; 
}
.icon{
    font-size: 20px;
    margin-right: 20px; 
    color: rgb(0, 0, 0);
}
.botton1 {
  background-color: rgb(221, 219, 255);
  color: rgb(99, 91, 255);
  border: none;
  padding: 8px 16px;
  border-radius: 5px; 
  font-size: 14px;
  cursor: default !important; 
}
.botton1:hover {
  background-color: rgb(203, 200, 255);
}

</style>