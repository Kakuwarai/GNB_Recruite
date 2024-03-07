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
                        @click="$router.replace('/Activity/posting/posting')">Posting</a>
                </div>
            </li>
            <li aria-current="page">
                <div class="flex items-center">
                    <svg class="w-3 h-3 mx-1 text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 6 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m1 9 4-4-4-4" />
                    </svg>
                    <span class="ml-1 text-sm font-medium  md:ml-2 text-gray-400">Edit Posting</span>
                </div>
            </li>
        </ol>
    </nav>

    <br>

    <div class="flex flex-wrap" v-loading="loadingSave"
        :element-loading-spinner="svg" element-loading-svg-view-box="-10, -10, 50, 50" 
        element-loading-background="rgba(255, 255, 255, 0.8)" style="width: 100%">
        <div class="w-full rounded-3xl bg-white p-6 ">


            <div aria-label="A complete example of page header">
                <el-page-header @back="onBack">

                    <template #content>
                        <div class="flex items-center">

                            <span class="text-large font-600 mr-3"> Posting </span>

                            <el-tag type="danger">Add</el-tag>
                        </div>
                    </template>
                </el-page-header>
            </div>
            <br>

            <el-form :label-position="labelPosition" ref="formRef" :model="numberValidateForm" label-width="130px">
                <div class="grid gap-4 sm:grid-cols-2 sm:gap-6">
                    <div class="w-full">

                        <el-form-item label="Job Type" prop="job" :rules="[
                            { required: true, message: 'Code is required' },
                            // { type: 'string', message: 'age must be a number' },
                        ]">
                            <el-select v-model.number="numberValidateForm.job" filterable placeholder="Select"
                                style="width: 240px">
                                <el-option v-for="item in jobList" :key="item.code" :label="item.name" :value="item.code" />

                            </el-select>
                        </el-form-item>

                        <el-form-item label="Languages" prop="language" :rules="[
                            { required: true, message: 'Languages is required' },
                            // { type: 'string', message: 'age must be a number' },
                        ]">

                            <el-select v-model.number="numberValidateForm.language" multiple filterable allow-create
                                default-first-option placeholder="Select">
                                <el-option v-for="item in languageList" :key="item.code" :label="item.name"
                                    :value="item.code" />

                            </el-select>
                        </el-form-item>

                        <el-form-item label="Responsibility" prop="responsibility" :rules="[
                            { required: true, message: 'Responsibility is required' },
                            //{ type: 'number', message: 'Salary must be a number' },
                        ]">
                            <el-input v-model.number="numberValidateForm.responsibility" :autosize="{ minRows: 2, maxRows: 4 }"
                                type="textarea" autocomplete="off" />
                        </el-form-item>
                        
                        <el-form-item label="Requirements" prop="requirements" :rules="[
                            { required: true, message: 'Requirements is required' },
                            //{ type: 'number', message: 'Salary must be a number' },
                        ]">
                            <el-input v-model.number="numberValidateForm.requirements"
                                :autosize="{ minRows: 2, maxRows: 4 }" type="textarea" autocomplete="off" />
                        </el-form-item>


                        <el-form-item label="Description" prop="description" :rules="[
                            { required: true, message: 'Description is required' },
                            //{ type: 'number', message: 'Salary must be a number' },
                        ]">
                            <el-input v-model.number="numberValidateForm.description" :autosize="{ minRows: 2, maxRows: 4 }"
                                type="textarea" autocomplete="off" />
                        </el-form-item>
                       


                    </div>

                    <div class="w-full">

                        <el-form-item label="Location" prop="location"  :rules="[
                            { required: true, message: 'Location is required' },
                           
                        ]">
                            <el-input v-model.number="numberValidateForm.location" type="text" autocomplete="off" />
                        </el-form-item>

                        <el-form-item label="Position Count" prop="positionNumber"  style="width: 240px" :rules="[
                            { required: true, message: 'Count is required' },
                             { type: 'number', message: 'Count must be a number' },
                        ]">
                            <el-input v-model.number="numberValidateForm.positionNumber" type="text" autocomplete="off" />
                        </el-form-item>
                        <div class="grid grid-flow-col auto-cols-max ">
                            <el-form-item  label="Currency" prop="currency" :rules="[
                                { required: true, message: 'Position is required' },
                                // { type: 'string', message: 'age must be a number' },
                            ]">
                                    <el-select v-model.number="numberValidateForm.currency" filterable placeholder="Select"
                                style="width: 100px">
                                <el-option v-for="item in currencies" :key="item.code" :label="item" :value="item" />

                            </el-select>
                            </el-form-item>
                            &nbsp;
                            &nbsp;
                        
                            <el-form-item label="Per" prop="per" :rules="[
                                { required: true, message: 'Per is required' },
                               
                            ]">
                            <el-select v-model.number="numberValidateForm.per" filterable placeholder="Select"
                            style="width: 100px">
                            <el-option v-for="item in perList" :key="item.code" :label="item" :value="item" />

                        </el-select>
                            </el-form-item>
                           
                         
                        </div>
                        <div class="grid grid-flow-col auto-cols-max ">
                            <el-form-item label="From" prop="salaryFrom" :rules="[
                                { required: true, message: 'Salary is required' },
                                { type: 'number', message: 'Salary must be a number' },
                            ]">
                                <el-input v-model.number="numberValidateForm.salaryFrom" type="text" autocomplete="off" />
                            </el-form-item>
                            &nbsp; &nbsp;
                            <el-form-item label="To" prop="salaryTo" :rules="[
                                { required: true, message: 'Salary is required' },
                                { type: 'number', message: 'Salary must be a number' },
                            ]">
                                <el-input v-model.number="numberValidateForm.salaryTo" type="text" autocomplete="off" />
                            </el-form-item>
                            </div>
                    <el-form-item label="Type" prop="type" :rules="[
                            { required: true, message: 'Type is required' },
                            // { type: 'string', message: 'age must be a number' },
                        ]">
                            <el-select v-model.number="numberValidateForm.type" filterable placeholder="Select"
                                style="width: 240px">
                                <el-option v-for="item in typeList" :key="item" :label="item" :value="item" />

                            </el-select>
                        </el-form-item>
                    </div>


                </div>

                <br>
                <h1>Recruiters</h1>
                <hr>


                <div v-for="data,index in numberValidateForm.language">

                    <el-form-item  :label="languageList.filter((x) => x.code == data)[0].name" prop="recruiter" :rules="[
                        { required: true, message: `One or more recruiter is required` },
                        // { type: 'string', message: 'age must be a number' },
                    ]">

                        <el-select v-model.name="numberValidateForm.recruiter[index]" multiple filterable allow-create
                            default-first-option placeholder="Select">
                            <el-option v-for="item in userlanguages.filter((x) => x.langCode == data)" :key="item.id" :label="item.fullname"
                                :value="item.id" />

                        </el-select>
                    </el-form-item>


                </div>

            </el-form>
            <br>
       
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
<!-- <button @click="test()">test</button> -->

        </div>
    </div>
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
const text = `
        <path class="path" d="
          M 30 15
          L 28 17
          M 25.61 25.61
          A 15 15, 0, 0, 1, 15 30
          A 15 15, 0, 1, 1, 27.99 7.5
          L 15 15
        " style="stroke-width: 4px; fill: rgba(0, 0, 0, 0);stroke: red;"/>
      `
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
    Note = ref(`*Note use {{Parameter}} if using parameters, maximum of 2`),
    labelPosition = ref('top'),
    userDetails = ref(JSON.parse(localStorage.getItem('login'))),
    editDetails = ref(JSON.parse(localStorage.getItem('editTerms'))),
    loadingSave = ref(false),
    //userDetails = ref(JSON.parse(localStorage.getItem('login'))),
    onBack = () => {
        router.replace('/Activity/posting/posting')
    },
    numberValidateForm = ref({
        job: '',
        language: [],
        positionNumber: '',
        currency: '',
        per:'',
        salaryFrom: '',
        salaryTo:'',
        responsibility:'',
        description: '',
        requirements: '',
        recruiter:  ([]),
        loacation: '',
        type: ''
    }),
    userlanguages = ref([]),
    jobList = ref([]),
    languageList = ref([]),
    typeList = ref([
        "Full Time",
        "Part Time"
        
    ]),
    perList = ref([
        "Hour", 
        "Month",
        "Year",
    ])
   

onMounted(async () => {
loadingSave.value = true
    await globalAPI().get(`Posting/lanJob`)
        .then(async (response) => {

            if (response.status == 200) {
                
                jobList.value = response.data.jobType    
                languageList.value = response.data.language       
                userlanguages.value = response.data.userlanguages

                const tempSalary = editDetails.value.salary.split('-')
                const tempLanguage = ref(JSON.parse(editDetails.value.languageCodes))

                numberValidateForm.value.job = editDetails.value.jobCode
                numberValidateForm.value.language =  tempLanguage.value
                numberValidateForm.value.requirements = editDetails.value.requirements
                numberValidateForm.value.responsibility = editDetails.value.responsibility
                numberValidateForm.value.description = editDetails.value.description
                numberValidateForm.value.positionNumber = editDetails.value.positionCount
                numberValidateForm.value.currency = editDetails.value.currency
                numberValidateForm.value.per = editDetails.value.per
                numberValidateForm.value.salaryFrom = parseInt(tempSalary[0])
                numberValidateForm.value.salaryTo = parseInt(tempSalary[1])
                numberValidateForm.value.location = editDetails.value.location
                numberValidateForm.value.type = editDetails.value.type

                const index = ref(0)
            //console.log(editDetails.value.asign.filter(x => x.languageCode == 'PH')[0].userId)
                tempLanguage.value.forEach(item => {
                  const itemTemp = ref([])
                  editDetails.value.asign.filter(x => x.languageCode == item).forEach(element => {
                    itemTemp.value.push(element.userId)
                 });

                    numberValidateForm.value.recruiter[index.value] = itemTemp.value
                    index.value = index.value + 1
                });
                
               
                // slawStatusPopUp('Successfully added')

            }
            else if (response.status == 202 || response.status == 401) {


                slawStatusPopUpError(response.data)

            } else {

                slawStatusPopUpError(response.data)
            }
            loadingSave.value = false

        }).catch((error) => {
            loadingSave.value = false
            swalPopUp(error, "Can't connect to server")

        })
})

function test(){
    console.log(numberValidateForm.value.recruiter);
}
async function savebutton() {
    loadingSave.value = true
   console.log(numberValidateForm.value.recruiter);
    await globalAPI().post(`Posting/editPosting?tagUsers=${JSON.stringify(numberValidateForm.value.recruiter)}`,  {
    id: editDetails.value.id,
    jobCode: numberValidateForm.value.job,
    jobType: jobList.value.filter((x) => x.code == numberValidateForm.value.job )[0].name,
    languageCodes: JSON.stringify(numberValidateForm.value.language),
    positionCount: numberValidateForm.value.positionNumber,
    currency: numberValidateForm.value.currency,
    per: numberValidateForm.value.per,
    salary: `${numberValidateForm.value.salaryFrom}-${numberValidateForm.value.salaryTo}`,
    location: numberValidateForm.value.location,
    type: numberValidateForm.value.type,
    responsibility: numberValidateForm.value.responsibility,
    description: numberValidateForm.value.description,
    requirements: numberValidateForm.value.requirements,
    modifiedBy: userDetails.value.id,
    status: 1
    }
    )
            .then(async (response) => {

                if (response.status == 200) {

                    slawStatusPopUp('Successfully added')
                    router.replace('/Activity/posting/posting')
                }
                else if (response.status == 202 || response.status == 401) {


                    slawStatusPopUpError(response.data)

                } else {

                    slawStatusPopUpError(response.data)
                }
                loadingSave.value = false

            }).catch((error) => {
                loadingSave.value = false
                swalPopUp(error, "Can't connect to server")

            })
}


const currencies = ref([
    "ADB Unit of Account",
"Afghani",
"Algerian Dinar",
"Argentine Peso",
"Armenian Dram",
"Aruban Florin",
"Australian Dollar",
"Azerbaijanian Manat",
"Bahamian Dollar",
"Bahraini Dinar",
"Balboa",
"Barbados Dollar",
"Belarussian Ruble",
"Belize Dollar",
"Bermudian Dollar",
"Bolivar",
"Brazilian Real",
"Brunei Dollar",
"Bulgarian Lev",
"Burundi Franc",
"CFA Franc BCEAO",
"CFA Franc BEAC",
"CFP Franc",
"Canadian Dollar",
"Cape Verde Escudo",
"Cayman Islands Dollar",
"Chilean Peso",
"Colombian Peso",
"Comoro Franc",
"Congolese Franc",
"Convertible Mark",
"Cordoba Oro",
"Costa Rican Colon",
"Croatian Kuna",
"Cuban Peso",
"Czech Koruna",
"Dalasi",
"Danish Krone",
"Djibouti Franc",
"Dobra",
"Dominican Peso",
"Dong",
"East Caribbean Dollar",
"Egyptian Pound",
"El Salvador Colon",
"Ethiopian Birr",
"Euro",
"Falkland Islands Pound",
"Fiji Dollar",
"Forint",
"Ghana Cedi",
"Gibraltar Pound",
"Gourde",
"Guarani",
"Guinea Franc",
"Guyana Dollar",
"Hong Kong Dollar",
"Hryvnia",
"Iceland Krona",
"Indian Rupee",
"Indonesian Rupiah",
"Iranian Rial",
"Iraqi Dinar",
"Israeli New Shekel",
"Jamaican Dollar",
"Japanese Yen",
"Jordanian Dinar",
"Kenyan Shilling",
"Kina",
"Kip",
"Kuwaiti Dinar",
"Kyat",
"Lari",
"Lebanese Pound",
"Lek",
"Lempira",
"Leone",
"Liberian Dollar",
"Libyan Dinar",
"Lilangeni",
"Loti",
"Malagasy Ariary",
"Malaysian Ringgit",
"Mauritius Rupee",
"Mexican Peso",
"Mexican Unidad de Inversion (UDI)",
"Moldovan Leu",
"Moroccan Dirham",
"Mvdol",
"Nakfa",
"Namibia Dollar",
"Nepalese Rupee",
"New Israeli Sheqel",
"New Taiwan Dollar",
"New Zealand Dollar",
"Ngultrum",
"Nigerian Naira",
"North Korean Won",
"Norwegian Krone",
"Nuevo Sol",
"Ouguiya",
"Pa’anga",
"Pakistani Rupee",
"Pataca",
"Peso Convertible",
"Peso Uruguayo",
"Philippine Peso",
"Pound Sterling",
"Qatari Rial",
"Quetzal",
"Rand",
"Rial Omani",
"Romanian Leu",
"Russian Ruble",
"Rwanda Franc",
"SDR (Special Drawing Right)",
"Saint Helena Pound",
"Saudi Riyal",
"Serbian Dinar",
"Seychelles Rupee",
"Singapore Dollar",
"Solomon Islands Dollar",
"Som",
"Somali Shilling",
"Somoni",
"South Sudanese Pound",
"Sri Lanka Rupee",
"Sudanese Pound",
"Surinam Dollar",
"Swedish Krona",
"Swiss Franc",
"Syrian Pound",
"Taka",
"Tala",
"Tanzanian Shilling",
"Tenge",
"Trinidad and Tobago Dollar",
"Tugrik",
"Tunisian Dinar",
"Turkish Lira",
"Turkmenistan New Manat",
"UAE Dirham",
"US Dollar",
"Uganda Shilling",
"Unidad de Fomento",
"Unidad de Valor Real",
"Uruguay Peso en Unidades Indexadas (URUIURUI)",
"Uzbekistan Sum",
"Vatu",
"Won",
"WIR Euro",
"WIR Franc",
"Yemeni Rial",
"Yen",
"Yuan Renminbi",
"Zambian Kwacha",
"Zimbabwe Dollar"
])
</script>

<!-- <style>
$colors: () !default;
$colors: map.deep-merge(
  (
    'white': #ffffff,
    'black': #000000,
    'primary': (
      'base': #ff4240,
    ),
    'success': (
      'base': #67c23a,
    ),
    'warning': (
      'base': #e6a23c,
    ),
    'danger': (
      'base': #f56c6c,
    ),
    'error': (
      'base': #f56c6c,
    ),
    'info': (
      'base': #909399,
    ),
  ),
  $colors
);
</style> -->