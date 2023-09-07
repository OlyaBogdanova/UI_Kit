<template>
  <div class="container">
    <div class="sidebar-toggle" @click="toggleMenu">&#5125</div>
    <layout-header/>
    <layout-sidebar :openSidebar="isOpenMenu" @closeSidebar="closeSideBar"/>
    <div :class="['content', {'content_full':!isOpenMenu}]">
      <router-view />
    </div>
  </div>
</template>

<script setup>
import LayoutHeader from "@/components/layout/Header.vue";
import LayoutSidebar from '@/components/layout/Sidebar.vue'
import { ref } from "vue";
const isOpenMenu=ref(false)
const toggleMenu=()=>{
  isOpenMenu.value=!isOpenMenu.value
}
function closeSideBar(){
  isOpenMenu.value=false
}
</script>

<style lang="scss">
@import "./styles/global.scss";
.content{
  max-width: 1400px;
  margin-left: 250px;
  padding: 45px 30px 30px;
  transition: 0.2s;
  &_full{
    margin-left: 0px;
  }
}
.sidebar-toggle{
  position: fixed;
  left: 0;
  top: 62px;
  width: 15px;
  background: var(--primary);
  height: 100%;
  z-index: 6;
  cursor: pointer;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;

}
.line {
  display: flex;
  margin-bottom: 20px;
  flex-wrap: wrap;
  &_block{
    flex-direction: column;
    p{
      margin-bottom: 15px;
    }
  }
}

@media screen and (max-width:1023px){
  .content{
    margin-left: 0;
  }
  
}
</style>
