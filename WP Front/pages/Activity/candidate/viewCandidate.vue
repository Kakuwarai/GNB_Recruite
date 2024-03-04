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
            value:2,

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
        "Final Interview Passed"

    ]),
    dialogOverflowVisible = ref(false)
    const pdfUrl = ref(null)



onMounted(async () => {
    await test()
})


async function test(){
    await globalAPI().get(`Candidate/ImageViewer`, {
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

}



</script>