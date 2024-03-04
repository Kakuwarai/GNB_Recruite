<script setup>
const router = useRouter();
import 'element-plus/dist/index.css'
import {
   UploadFilled,
   Tickets,
   Notebook,
   Suitcase,
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



onMounted(() => {

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

   if(menu == 3){
      router.replace('/activity/aTransaction/transaction')
   }
   if(menu == 4){
      router.replace('/maintenance/mUsers/users')
   }
   if(menu == 5){
      router.replace('/maintenance/mBranches/branches')
   }
   if(menu == 6){
      router.replace('/maintenance/mMenus/menu')
   }
   if(menu == 7){
      router.replace('/maintenance/mCustomer/customer')
   }
   if(menu == 8){
      router.replace('/maintenance/mCharges/charges')
   }
   if(menu == 9){
      router.replace('/maintenance/mTerms/terms')
   }
   if(menu == 10){
      router.replace('/maintenance/mPosition/position')
   }

}
function cDashboard() {
   router.push('/dashboard')
}


const handleClose = (key, keyPath) => {
  
};
</script>

<template>
  

   <el-menu  active-text-color="#ff0000" class="" default-active="2" text-color="#bbbbbbb" @open="handleOpen"
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
       </el-sub-menu>
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
   </el-menu>
  
</template>

