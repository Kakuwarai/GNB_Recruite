<template>
    <!-- Breadcrumb -->
    <nav class="flex px-5 py-3 text-gray-700 border border-gray-200 rounded-lg bg-gray-50" aria-label="Breadcrumb">
        <ol class="inline-flex items-center space-x-1 md:space-x-3">
            <li class="inline-flex items-center">
                <a href="#" class="inline-flex items-center text-sm font-medium text-gray-700 hover:text-blue-60">
                    <svg class="w-3 h-3 mr-2.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor"
                        viewBox="0 0 20 20">
                        <path
                            d="m19.707 9.293-2-2-7-7a1 1 0 0 0-1.414 0l-7 7-2 2a1 1 0 0 0 1.414 1.414L2 10.414V18a2 2 0 0 0 2 2h3a1 1 0 0 0 1-1v-4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v4a1 1 0 0 0 1 1h3a2 2 0 0 0 2-2v-7.586l.293.293a1 1 0 0 0 1.414-1.414Z" />
                    </svg>
                    Home
                </a>
            </li>
            <li aria-current="page">
                <div class="flex items-center">
                    <svg class="w-3 h-3 mx-1 text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 6 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m1 9 4-4-4-4" />
                    </svg>
                    <span class="ml-1 text-sm font-medium  md:ml-2 text-gray-400">Maintenance</span>
                </div>
            </li>
            <!-- <li>
          <div class="flex items-center">
            <svg class="w-3 h-3 mx-1 text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
            </svg>
            <a href="#" class="ml-1 text-sm font-medium text-gray-700 hover:text-blue-600 md:ml-2 text-gray-400 hover:text-white">Templates</a>
          </div>
        </li> -->
            <li aria-current="page">
                <div class="flex items-center">
                    <svg class="w-3 h-3 mx-1 text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 6 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m1 9 4-4-4-4" />
                    </svg>
                    <span class="ml-1 text-sm font-medium  md:ml-2 text-gray-400">Candidates</span>
                </div>
            </li>
        </ol>
    </nav>

    <br>

    <div class="flex flex-wrap">
        <div class="w-full rounded-3xl bg-white p-6 shadow :bg-gray-900">


            <!-- component -->

            <el-select  v-model="jobSelected" filterable placeholder="Select Job" style="width: 240px" >
                <el-option v-for="item in jobList" :key="item.code" :label="item.name" :value="item.code" @click="addTab(jobSelected)"/>

            </el-select>
<br><br>
            <!--  -->
      
            <el-tabs  @click="event => {jobCandidates(editableTabsValue),changeTabColor(targetName)}" v-model="editableTabsValue" type="card" class="demo-tabs" closable @tab-remove="removeTab">
                <el-tab-pane v-for="item in editableTabs" :key="item.name" :label="item.title" :name="item.name"  
                >
                    
                    <!-- content -->    
                    <div class="mt-1 relative overflow-x-auto shadow-md sm:rounded-lg">
                        <table class="w-full text-sm text-left text-gray-500 ">
                            <thead class="text-xs text-gray-700 uppercase bg-gray-50 ">
                                <tr>
                                    <th scope="col" class="px-6 py-3">
                                        Name
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Email
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        POLO/NON-POLO
                                    </th>
                                    <th scope="col" class="px-6 py-3 ">
                                        Status
                                    </th>
                                    <th scope="col" class="px-6 py-3 text-right">
                                        View
                                    </th>
                                </tr>
                            </thead>
                            <tbody v-if="tblLoading == false">
                                <tr v-for="data in jobCandidateList" class="bg-white border-b  hover:bg-gray-50 ">
                                    <td class="px-6 py-4">
                                        {{ `${data.firstname} ${data.middlename} ${data.lastname}` }} 
                                    </td>
                                    <td class="px-6 py-4">
                                        {{ data.email }}
                                    </td>
                                    <td class="px-6 py-4 max-w-96">
                                        {{ data.polo == 0? "Non-Polo" : "Polo" }}
                                    </td>
                                    <td class="px-6 py-4">
                                        <span 
                                            class="bg-blue-100 text-blue-800 text-xs font-medium mr-2 px-2.5 py-0.5 rounded border border-blue-400">
                                            {{ data.statusDescription }}
                                        </span>
                                          
                                    </td>
                                    <td class="px-6 py-4 text-right">
                                        <button type="button" @click="view(data)"
                                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm p-1.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                                            <svg class="h-4 w-4 text-white-500"  fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
                                              </svg>
                                              
                                        </button>
                                    </td>
                                </tr>
          
                            </tbody>
          
                            <tbody v-else>
                                <tr v-for="index in 6">
          
                                    <td role="status" class="max-w-sm animate-pulse">
                                        <div class=" h-7 bg-gray-200 rounded-lg m-2"></div>
                                    </td>
                                    <td role="status" class="max-w-sm animate-pulse">
                                        <div class=" h-7 bg-gray-200 rounded-lg m-2"></div>
                                    </td>
                                    <td role="status" class="max-w-sm animate-pulse">
                                        <div class=" h-7 bg-gray-200 rounded-lg m-2"></div>
                                    </td>
                                    <td role="status" class="max-w-sm animate-pulse">
                                        <div class=" h-7 bg-gray-200 rounded-lg m-2"></div>
                                    </td>
                                    <td role="status" class="max-w-sm animate-pulse">
                                        <div class=" h-7 bg-gray-200 rounded-lg m-2"></div>
                                    </td>
                                    <td role="status" class="max-w-sm animate-pulse">
                                        <div class=" h-7 bg-gray-200 rounded-lg m-2"></div>
                                    </td>
          
                                </tr>
          
                            </tbody>
          
                        </table>
                        <el-empty v-if="jobCandidateList == '' && tblLoading == false" :image-size="200" />
                    </div>
                    <!-- content end -->

                </el-tab-pane>
            </el-tabs>

        </div>
    </div>
</template>
    
<script setup>
import Swal from 'sweetalert2';
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
import { globalAPI, swalPopUp, swalLoad, slawStatusPopUpError, slawStatusPopUpWarning } from '@/services/globalFunctions'

const router = useRouter(),
    userDetails = ref(JSON.parse(localStorage.getItem('login'))),
    tblLoading = ref(false),
    jobCandidateList = ref([])


onMounted(() => {
    console.log(localStorage.getItem("selectedJob")??[]);
    getDetails()
})
let tabIndex = 2;
const jobList = ref([]),
    jobMultiSelected = ref([]),
    jobSelected = ref(''),
editableTabsValue = ref('2'),
editableTabs = ref(JSON.parse(localStorage.getItem("selectedJob"))??[]),
addTab = (targetName) => {
    jobSelected.value = null

if (editableTabs.value.filter(x => x.name == targetName).length == 0) {
    const newTabName = `${++tabIndex}`;
  editableTabs.value.push({
    title: jobList.value.filter(x => x.code == targetName)[0].name,
    name: targetName,
  
  });
  editableTabsValue.value = newTabName;

  localStorage.setItem("selectedJob", JSON.stringify(editableTabs.value))

}else{
    slawStatusPopUpWarning("Already Added!")
}

  
},
removeTab = (targetName) => {
  const tabs = editableTabs.value;
  let activeName = editableTabsValue.value;
  if (activeName === targetName) {
    tabs.forEach((tab, index) => {
      if (tab.name === targetName) {
        const nextTab = tabs[index + 1] || tabs[index - 1];
        if (nextTab) {
          activeName = nextTab.name;
        }
      }
    });
  }

  editableTabsValue.value = activeName;
  editableTabs.value = tabs.filter((tab) => tab.name !== targetName)
  localStorage.setItem("selectedJob", JSON.stringify(editableTabs.value))
}


async function getDetails() {

    await globalAPI().get(`Candidate/jobTypeList`)
        .then(async (response) => {

            if (response.status == 200) {

                jobList.value = response.data
                

            }
            else if (response.status == 202 || response.status == 401) {


                slawStatusPopUpError(response.data)

            } else {

                slawStatusPopUpError(response.data)
            }


        }).catch((error) => {

            swalPopUp(error, "Can't connect to server")

        })
}


async function jobCandidates(){


    await globalAPI().get(`Candidate/jobCandidates?userId=${userDetails.value.id}&jobCode=${editableTabsValue.value}`)
        .then(async (response) => {

            if (response.status == 200) {

                jobCandidateList.value = response.data
          

            }
            else if (response.status == 202 || response.status == 401) {

                jobCandidateList.value = []
                slawStatusPopUpWarning(response.data)

            } else {

                slawStatusPopUpError(response.data)
            }


        }).catch((error) => {

            swalPopUp(error, "Can't connect to server")

        })

}
const activeTab = ref(null)
const changeTabColor = (tabName) => {
    
  activeTab.value = tabName;
}

function view(data){
    sessionStorage.setItem("candidateData",JSON.stringify(data))
    router.replace('/Activity/candidate/viewCandidate')
}
</script>


