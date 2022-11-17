
<template>
  <v-main>
    
    <SubHeading content="Create Resume content"/>
    <v-form
    ref="form"
    v-model="valid"
    lazy-validation
    >
    <BasicAccordion @primary="getPrimaryDetails"/>
    <AddressAccordion @address="getAddressDetails"/>
    <EducationAccordion @education="getEducationDetails"/>
    <ExperienceAccordion @experience="getExperienceDetails"/>
    <ProjectAccordion @project="getProjectDetails"/>
    <SkillAccordion @skill="getSkillDetails"/>
    <SocialAccordion @social="getSocialDetails"/>
    <SkillTest/>
    <v-row>
      <v-btn class="mb-5 mt-3 teal" dark @click="create_resume" id="">
        Save
      </v-btn>
      <v-btn class="mb-5 mt-3 ml-3"   id="">
        Cancel
      </v-btn>
    </v-row>
  </v-form>
    
  </v-main> 
  
  

</template>

<script>

import SubHeading from '../components/accordiontitle.vue'
import BasicAccordion from '../components/basic_accordion.vue'
import AddressAccordion from '../components/address_accordion.vue'
import EducationAccordion from '../components/education_accordion.vue'
import ExperienceAccordion from '../components/experience_accordion.vue'
import ProjectAccordion from '../components/project_accordion.vue'
import SkillAccordion from '../components/skill_accordion.vue'
import SocialAccordion from '../components/social_accordion.vue'
import axios from 'axios'


  export default {
    name: 'accordionForm',

    components:{
      
      SubHeading,
      BasicAccordion,
      AddressAccordion,
      EducationAccordion,
      ExperienceAccordion,
      ProjectAccordion,
      SkillAccordion,
      SocialAccordion, 
      
    },
    data() {
      return{
        name:'',
        email: '',
        phone:'',
        image:'',
        summary:'',
        House_name:'',
        Street:'',
        City:'',
        pincode:'',
        Country:'',
        item:[],
        education:[],
        experience:[],
        skill:[],
        project:[],
        social:[],
        alert:false

      }
    },
    methods:{
    getPrimaryDetails(data) {
      console.log("Basic details >>>>", data)
      this.name=data.name
      this.email=data.email
      this.phone=data.phone
      this.image=data.image
      this.summary=data.summary
      console.log(this.email);
    },
    getAddressDetails(data){
      this.House_name = data.House_name
      this.Street = data.Street
      this.City = data.City
      this.pincode = data.pincode
      this.Country = data.Country
    },
    getEducationDetails(data){
      

      console.log("edu",data);

      this.education = data
      console.log("eduu",this.education);
    },
    getExperienceDetails(data){
      
      console.log("exp:",data)

      this.experience = data

      
    },
    
    getProjectDetails(data){
      // this.project_title = data.project_title
      // this.project_description = data.project_description
      console.log("projectname :",data)
      this.project = data

    },
    getSkillDetails(data){
      console.log("skl check")
      console.log("skl data",data)
      this.skill = data
     
    },
    getSocialDetails(data){
      // this.platform = data.platform
      // this.username = data.username
      // this.social_URL = data.social_URL

      this.social = data
    },

    async create_resume(){
      console.log("Hello")
        const primaryDetails = {
            name: this.name,
            email: this.email,
            phone: this.phone,
            image_URL:this.image,
            summary:this.summary,
            address_details:[
              {
                House_name:this.House_name,
                Street:this.Street,
                City:this.City,
                pincode:this.pincode,
                Country:this.Country
              }
            ],
            education_details:this.education,
            experience_details:this.experience,
            project_details:this.project,
            skill_details:this.skill,
            social_details:this.social
          }
    console.log("varunnundonn nokk");     
    console.log(primaryDetails);
    await axios.post(`http://127.0.0.1:8000/new_resume`,primaryDetails).then((res)=>{
      this.alert=true
      console.log(res.data)
    }).catch((err)=>{
      console.log(err);
    })
  }
}
  }
</script>




<style>
.row{
  margin:0px 20px;
}
.v-form{
  margin-top: 20px;
}
.v-application a {
  color: black;
}


</style>
