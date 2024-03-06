<script setup>
const router = useRouter();
import 'element-plus/dist/index.css'
import {
   UploadFilled,
   Tickets,
   Notebook,
   Suitcase,
   UserFilled,
   Folder,
   Menu as IconMenu,
   Avatar,
   User,
   Setting,
   OfficeBuilding,
   Collection,
   List,
   Briefcase
} from '@element-plus/icons-vue'
import { initFlowbite } from 'flowbite'

const parent = ref(JSON.parse(localStorage.getItem("parentMenu"))),
menuList = ref(JSON.parse(localStorage.getItem("childMenu")))

onMounted(() => {
console.log(parent.value)
console.log(menuList.value)
   window.addEventListener('menuChange', () => {
      //userMenus.value = localStorage.getItem('menus').toString() == 'undefined' ? 'undefined' : JSON.parse(localStorage.getItem('menus'))
      menuList.value = JSON.parse(localStorage.getItem('menuList'))
      parent.value = JSON.parse(localStorage.getItem('parent'))
      
      //theMenus()
      initFlowbite();
   });
   //theMenus()
   initFlowbite();
   
})




function selectMenus(menu){

   if(menu == 2){
      router.replace('/Activity/posting/posting')
   }
   if(menu == 3){
      router.replace('/Activity/candidate/candidate')
   }
   if(menu == 4){
      router.replace('/Activity/progress/progress')
   }
   if(menu == 6){
      router.replace('/Maintenance/users/users')
   }
   if(menu == 7){
      router.replace('/Maintenance/Job/Job')
   }
   if(menu == 8){
      router.replace('/Maintenance/menu/menu')
   }

}
function cDashboard() {
   router.push('/dashboard')
}


const handleClose = (key, keyPath) => {
  
};
</script>

<template>
  
   <el-menu  active-text-color="red" class="" default-active="2" text-color="#bbbbbbb" @open="handleOpen"
   @close="handleClose">
   <el-menu-item index="1" @click="$router.replace('/dashboard')">
      <el-icon><icon-menu /></el-icon>
      <span>Dashboard</span>
    </el-menu-item>
   <div v-for="item,index in parent">
<el-sub-menu  :index="index + 1" >
      <template #title>
         <el-icon>
            <Tickets v-if="item.id == 1"/>
            <Setting v-if="item.id == 5"/>
         </el-icon>
         <span> {{item.name}} </span>
      </template>
<div v-for="nextItem,nextIndex in menuList.filter(x => x.parentId == item.id)">
      <el-menu-item  :index="`${index + 1}-${nextIndex + 1}`" @click="selectMenus(nextItem.id)">
         <el-icon>
            <UploadFilled v-if="nextItem.id == 2" />
            <Avatar v-if="nextItem.id == 3"/>
            <!-- <Briefcase /> -->
            <Avatar v-if="nextItem.id == 4"/>
            <User v-if="nextItem.id == 6"/>
            <Suitcase v-if="nextItem.id == 7 "/>
            <Collection v-if="nextItem.id == 8"/>
            <!-- <Briefcase v-if="nextItem.id == 9"/> -->
         </el-icon>
         {{ nextItem.name }} </el-menu-item></div>
   </el-sub-menu>
</div>
</el-menu>


   <!-- <el-menu  active-text-color="#ff0000" class="" default-active="2" text-color="#bbbbbbb" @open="handleOpen"
      @close="handleClose">
      <el-menu-item index="1" @click="$router.replace('/dashboard')">
         <el-icon><icon-menu /></el-icon>
         <span>Dashboard</span>
       </el-menu-item>

       <el-sub-menu index="2">
         <template #title>
           <el-icon> <Tickets/></el-icon>
           <span>Activity</span>
         </template>
         <el-menu-item index="2-1" @click="$router.replace('/activity/posting/posting')">
            <el-icon><Notebook /></el-icon>
            Posting
         </el-menu-item>
         <el-menu-item index="2-2" @click="$router.replace('/activity/candidate/candidate')">
            <el-icon><Avatar /></el-icon>
            Candidates</el-menu-item>
            <el-menu-item index="2-3" @click="$router.replace('/activity/progress/progress')">
               <el-icon><Avatar /></el-icon>
               Progress</el-menu-item>   
       </el-sub-menu>

       <el-sub-menu index="3">
         <template #title>
            <el-icon><Setting /></el-icon>
           <span>Maintenance</span>
         </template>
         <el-menu-item index="3-1" @click="$router.replace('/Maintenance/users/users')">
            <el-icon><UserFilled /></el-icon>
            Users
         </el-menu-item>
         <el-menu-item index="3-2" @click="$router.replace('/Maintenance/job/job')">
            <el-icon><Folder /></el-icon>
            Job Type</el-menu-item>
            <el-menu-item index="3-3" @click="$router.replace('/activity/progress/progress')">
               <el-icon><Avatar /></el-icon>
               Menu</el-menu-item>   
       </el-sub-menu> 
       </el-menu>-->

   <!-- <el-sub-menu :index="index + 1" >
         <template #title>
            <el-icon>
               <Tickets v-if="item.id == 1"/>
               <Setting v-if="item.id == 2"/>
            </el-icon>
            <span> {{item.name}} </span>
         </template>
<div v-for="nextItem,nextIndex in menuList.filter(x => x.parentMenuId == item.id)">
         <el-menu-item  :index="`${index + 1}-${nextIndex + 1}`" @click="selectMenus(nextItem.id)">
            <el-icon>
               <UploadFilled v-if="nextItem.id == 3" />
               <User v-if="nextItem.id == 4"/>
             
               <OfficeBuilding v-if="nextItem.id == 5"/>
               <Suitcase v-if="nextItem.id == 7"/>
               <Collection v-if="nextItem.id == 8 || nextItem.id == 9 "/>
               <List v-if="nextItem.id == 6"/>
               <Briefcase v-if="nextItem.id == 10"/>
            </el-icon>
            {{ nextItem.name }} </el-menu-item></div>
      </el-sub-menu> -->
  
  
</template>

