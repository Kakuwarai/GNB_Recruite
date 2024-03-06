<template  >
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
                    <span class="ml-1 text-sm font-medium  md:ml-2 text-gray-400">Activity</span>
                </div>
            </li>
            <li>
                <div class="flex items-center">
                    <svg class="w-3 h-3 mx-1 text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 6 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m1 9 4-4-4-4" />
                    </svg>
                    <a class="cursor-pointer ml-1 text-sm font-medium text-gray-700  md:ml-2 "
                        @click="$router.replace('/Activity/candidate/candidate')">Candidates</a>
                </div>
            </li>
            <li aria-current="page">
                <div class="flex items-center">
                    <svg class="w-3 h-3 mx-1 text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 6 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m1 9 4-4-4-4" />
                    </svg>
                    <span class="ml-1 text-sm font-medium  md:ml-2 text-gray-400">View Candidate</span>
                </div>
            </li>
        </ol>
    </nav>

    <br>

    <div class="flex flex-wrap" v-loading="loadingSave" :element-loading-spinner="svg"
        element-loading-svg-view-box="-10, -10, 50, 50" element-loading-background="rgba(255, 255, 255, 0.8)"
        style="width: 100%">
        <div class="w-full rounded-3xl bg-white p-6 ">


            <div aria-label="A complete example of page header">
                <el-page-header @back="onBack">

                    <template #content>
                        <div class="flex items-center">

                            <span class="text-large font-600 mr-3"> Candidates </span>

                            <el-tag type="danger">View</el-tag>
                        </div>
                    </template>
                </el-page-header>
            </div>
            <br>
            <div class="flex justify-end ">
                <el-button plain @click="dialogOverflowVisible = true">
                    View Resume
                  </el-button>
            </div>
            <el-form :label-position="labelPosition" ref="formRef" :model="numberValidateForm" label-width="130px">
                <p class="text-xs text-gray-900 dark:text-white">Fullname</p>
                <hr>
                <div class="mt-2 grid gap-4 sm:grid-cols-2 sm:gap-6">
                    <div class="w-full">
                        
                        
                            <el-form-item label="Firstname" prop="firstname" :rules="[
                                { required: false, message: 'Firstname is required' },
    
                            ]">
                                <el-input v-model.number="numberValidateForm.firstname" type="text" autocomplete="off" disabled/>
                            </el-form-item>
    
                           
                            <el-form-item label="Lastname" prop="lastname" :rules="[
                                { required: false, message: 'Lastname is required' },
                              
                            ]">
                                <el-input v-model.number="numberValidateForm.lastname" type="text" autocomplete="off" disabled/>
                            </el-form-item>
                           
                          

                    </div>

                      <div class="w-full">
                                <el-form-item label="Middlename" prop="middlename"  :rules="[
                                    { required: false, message: 'Middlename is required' },
                                  
                                ]">
                                    <el-input v-model.number="numberValidateForm.middlename" type="text" autocomplete="off" disabled/>
                                </el-form-item>

                            </div>
                </div>

                <p class="text-xs text-gray-900 dark:text-white">Details</p>
                <hr>

                <div class="mt-2 grid gap-4 sm:grid-cols-2 sm:gap-6">
                    <div class="w-full">

                        <el-form-item label="Job Type" prop="jobType"  :rules="[
                            // { required: false, message: 'Middlename is required' },
                           
                         ]">
                             <el-input v-model.number="numberValidateForm.jobType" type="text" autocomplete="off" disabled/>
                         </el-form-item>

                        <el-form-item label="Country" prop="country"  :rules="[
                           // { required: false, message: 'Middlename is required' },
                          
                        ]">
                            <el-input v-model.number="numberValidateForm.country" type="text" autocomplete="off" disabled/>
                        </el-form-item>

                        <el-form-item label="Description" prop="description" :rules="[
                            { required: false, message: 'Description is required' },
                          
                        ]">
                        <el-select v-model.number="numberValidateForm.description" filterable placeholder="Select"
                        style="width: 240px">
                        <el-option v-for="item in descriptionList" :key="item" :label="item" :value="item" />
        
                    </el-select>
                        </el-form-item>

                      
                        </div>

                        <div class="w-full">

                            <el-form-item label="Polo" prop="polo" :rules="[
                                { required: false, message: 'Polo is required' },
                              
                            ]">
                            <el-select v-model.number="numberValidateForm.polo" filterable placeholder="Select"
                            style="width: 240px">
                            <el-option v-for="item in poloList" :key="item" :label="item.item" :value="item.value" />
            
                        </el-select>
                            </el-form-item>

                            <el-form-item label="Current Residing" prop="currentCountry"  :rules="[
                                //{ required: false, message: 'Current Residing is required' },
                              
                            ]">
                                <el-input v-model.number="numberValidateForm.currentCountry" type="text" autocomplete="off" disabled/>
                            </el-form-item>

                            <el-form-item label="Last Description" prop="lastDescription" :rules="[
                                { required: false, message: 'Last Description is required' },
                              
                            ]">
                            <el-select disabled="" v-model.number="numberValidateForm.lastDescription" filterable placeholder="Select"
                            style="width: 240px">
                            <el-option v-for="item in descriptionList" :key="item" :label="item" :value="item" />
            
                        </el-select>
                            </el-form-item>
                        </div>

                        </div>

               
            </el-form>
          
            <button type="button" @click="savebutton()" :disabled="loadingSave"
            class="text-white bg-[#3b984a] hover:bg-[#3b984a]/90 focus:ring-4 focus:outline-none focus:ring-[#3b984a]/50 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center :focus:ring-[#3b984a]/55 mr-2 mb-2">

            <svg v-if="loadingSave == true" aria-hidden="true"
                class="w-4 h-4 mr-2 text-gray-200 animate-spin :text-gray-600 fill-blue-600" viewBox="0 0 100 101"
                fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z"
                    fill="currentColor" />
                <path
                    d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z"
                    fill="currentFill" />
            </svg>

            <svg v-else class=" mr-1 h-4 w-4 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M19 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11l5 5v11a2 2 0 0 1-2 2z" />
                <polyline points="17 21 17 13 7 13 7 21" />
                <polyline points="7 3 7 8 15 8" />
            </svg>
            <span v-if="loadingSave"> Saving </span>
            <span v-else> Save </span>
            <svg v-if="loadingSave" version="1.1" xmlns="http://www.w3.org/2000/svg" width="15px" height="10px"
                viewBox="0 0 80 20">
                <circle cx="10" cy="20" r="10" fill="#FFFFFF">
                    <animate attributeName="cx" from="10" to="40" dur="0.5s" calcMode="spline"
                        keySplines="0.42 0 0.58 1" keyTimes="0;1" repeatCount="indefinite" />
                </circle>
                <circle cx="10" cy="10" r="0" fill="#FFFFFF">
                    <animate attributeName="r" from="0" to="10" dur="0.5s" calcMode="spline" keySplines="0.42 0 0.58 1"
                        keyTimes="0;1" repeatCount="indefinite" />
                </circle>
                <circle cx="40" cy="10" r="10" fill="#FFFFFF">
                    <animate attributeName="cx" from="40" to="70" dur="0.5s" calcMode="spline"
                        keySplines="0.42 0 0.58 1" keyTimes="0;1" repeatCount="indefinite" />
                </circle>
                <circle cx="70" cy="10" r="10" fill="#FFFFFF">
                    <animate attributeName="r" from="10" to="0" dur="0.5s" calcMode="spline" keySplines="0.42 0 0.58 1"
                        keyTimes="0;1" repeatCount="indefinite" />
                </circle>
            </svg>
        </button>

        </div>
    </div>


    <!-- Dialog PDF-->

    <el-dialog
    v-model="dialogOverflowVisible"
    :title="`${numberValidateForm.firstname} ${numberValidateForm.middlename} ${numberValidateForm.lastname}`"
    width="95%"
    draggable
    overflow
  >
  <div>
    <embed v-if="pdfUrl" :src="pdfUrl" type="application/pdf" width="100%" height="600px" />
    <div v-else>Loading PDF...</div>
  </div>
    <template #footer>
      <!-- <div class="dialog-footer">
        <el-button @click="dialogOverflowVisible = false">Cancel</el-button>
        <el-button type="primary" @click="dialogOverflowVisible = false">
          Confirm
        </el-button>
      </div> -->
    </template>
  </el-dialog>
</template>
  
<script setup>
//import './styles/element/index.scss'
import 'element-plus/dist/index.css'
import { ref } from "vue";
import { globalAPI, swalLoad, swalPopUp, slawStatusPopUpError, slawStatusPopUp } from '@/services/globalFunctions'
import Paginate from 'vuejs-paginate-next';
import Swal from 'sweetalert2';
const loadingElement = document.querySelector('[element-loading-text="Loading..."]');

// Check if the element exists
if (loadingElement) {
    // Change the text color
    loadingElement.style.color = "red"; // Change "red" to any color you prefer
}

const svg = `
        <path class="path" d="
          M 30 15
          L 28 17
          M 25.61 25.61
          A 15 15, 0, 0, 1, 15 30
          A 15 15, 0, 1, 1, 27.99 7.5
          L 15 15
        " style="stroke-width: 4px; fill: rgba(0, 0, 0, 0);stroke: red;"/>
      `, router = useRouter(),
    userDetails = ref(JSON.parse(localStorage.getItem('login'))),
    candidateData = ref(JSON.parse(sessionStorage.getItem("candidateData"))),
    labelPosition = ref('top'),
    loadingSave = ref(false),
    //userDetails = ref(JSON.parse(localStorage.getItem('login'))),
    onBack = () => {
        router.replace('/Activity/candidate/candidate')
    },
    numberValidateForm = ref({
        firstname: candidateData.value.firstname,
        middlename: candidateData.value.middlename,
        lastname: candidateData.value.lastname,
        polo: candidateData.value.polo,
        country: candidateData.value.countryName,
        currentCountry: candidateData.value.currentCountryName,
        description: candidateData.value.statusDescription,
        lastDescription: candidateData.value.lastStatusDescription,
        jobType: candidateData.value.jobTypeName,
        status: candidateData.value.status

    }),
    poloList = ref([
        {
            item:"Polo",
            value:1,

        },
        {
            item:"Non-Polo",
            value:0,

        }
    ]),
    descriptionList = ref([
        "New",
        "Fees & Terms Sent",
        "Waiting for Response",
        "Pre-screen Scheduled",
        "Pre-screen Passed",
        "Documents Received ",
        "Forwarded",
        "Final Interview Passed",
        "Progress",
        "Selected",
        "Not Selected"

    ]),
    dialogOverflowVisible = ref(false)
    const pdfUrl = ref(null)



onMounted(async () => {
    await getResumeAndAdmissibility()
})


async function getResumeAndAdmissibility(){

    loadingSave.value = true
    await globalAPI().get(`Candidate/getResumeAndAdmissibility?candidateId=${candidateData.value.id}`, {
          responseType: 'blob' // Set responseType to 'blob' to handle binary data
        })
        .then(async (response) => {

            if (response.status == 200) {

                const pdfBlob = new Blob([response.data], { type: 'application/pdf' })
                pdfUrl.value = URL.createObjectURL(pdfBlob)
          

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
        loadingSave.value = false
}

async function savebutton(){
console.log();
    await globalAPI().post(`Candidate/saveJobCandidate`,
    
    {
        id: candidateData.value.id,
        statusDescription: numberValidateForm.value.description,
        polo: numberValidateForm.value.polo
    })
        .then(async (response) => {

            if (response.status == 200) {

                slawStatusPopUp(response.data)
          

            }
            else if (response.status == 202 || response.status == 401) {

         
                slawStatusPopUpWarning(response.data)

            } else {

                slawStatusPopUpError(response.data)
            }


        }).catch((error) => {

            swalPopUp(error, "Can't connect to server")

        })

}


</script>