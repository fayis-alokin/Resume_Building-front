<template>
    <v-main>

        <subHeading content="Edit Resume content"/>
        <v-form
        ref="form"
        v-model="valid"
        lazy-validation
        >
        <BasicAccordion v-if="items.prim" :primary_details="items.prim[0]"  @primary="getPrimaryDetails"/>
        <AddressAccordion v-if="items.adrs" :address_details="items.adrs[0]" @address="getAddressDetails"/>
        <EducationAccordion v-if="items.edu" :education_details="items.edu" @education="getEducationDetails"/>
        <ExperienceAccordion v-if="items.exp" :experience_details="items.exp" @experience="getExperienceDetails"/>
        <ProjectAccordion v-if="items.prjct" :project_details="items.prjct[0]" @project="getProjectDetails"/>
        <SkillAccordion v-if="items.skl" :skill_details="items.skl[0]" @skill="getSkillDetails"/>
        <SocialAccordion v-if="items.sm" :social_details="items.sm[0]" @social="getSocialDetails"/>
        <v-row>
          <v-btn class="mb-5 teal" dark @click="edit_resume">
            Edit
          </v-btn>
          <v-btn class="mb-5 ml-3" >
            Cancel
          </v-btn>
        </v-row>
      </v-form>
    </v-main>
</template>

<script>
import subHeading from '../components/accordiontitle.vue' 
import BasicAccordion from '../components/basic_accordion.vue'
import AddressAccordion from '../components/address_accordion.vue'
import EducationAccordion from '../components/education_accordion.vue'
import ExperienceAccordion from '../components/experience_accordion.vue'
import ProjectAccordion from '../components/project_accordion.vue'
import SkillAccordion from '../components/skill_accordion.vue'
import SocialAccordion from '../components/social_accordion.vue'
import axios from 'axios'
export default{
    name:'EditResume',
    components:{
        subHeading,
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
        Qualification:'',
        Course_name:'',
        University_name:'',
        Location:'',
        passing_year:'',
        company_name:'',
        location:'',
        start_date:'',
        end_date:'',
        skill_name: "",
        skill_level: "",
        project_title:'',
        project_description:'',
        platform:'',
        username:'',
        social_URL:'',
        id: this.$route.params.id,
        items: [],
        education:[],
        experience:[],
        project:[],
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
        console.log("nokk")
        console.log(data)
        },
        getAddressDetails(data){
        this.House_name = data.House_name
        this.Street = data.Street
        this.City = data.City
        this.pincode = data.pincode
        this.Country = data.Country
        console.log(this.pincode)
        console.log(this.Street)
        },
        getEducationDetails(data){
          console.log("education data:",data)
          this.education = data
        },
        getExperienceDetails(data){
          // console.log("varunnund:")
          // console.log("Exp data:",data)
          // this.role = data.role
          // this.company_name = data.company_name
          // this.company_location = data.company_location
          // this.end_date = data.end_date

          this.experience = data
        },
        getProjectDetails(data){
          // console.log("project data:",data)
          // this.project_title = data.project_title
          // this.project_description = data.project_description
          // console.log(this.project_title)
          // console.log(data.project_title)

          this.project = data
        },
        getSkillDetails(data){
        this.skill_name = data.skill_name
        this.skill_level = data.skill_level
        },
        getSocialDetails(data){
        this.platform = data.platform
        this.username = data.username
        this.social_URL = data.social_URL
        },


        async edit_resume(){
        console.log("Hello")
            const primaryDetails = {
              
               prim:[
                {
                  name: this.name,
                  email: this.email,
                  phone: this.phone,
                  image_URL:this.image,
                  summary:this.summary,
                }
               ],
                adrs:[
                {
                    House_name:this.House_name,
                    Street:this.Street,
                    City:this.City,
                    pincode:this.pincode,
                    Country:this.Country
                }
                ],
                edu:this.education,
                exp:this.experience,
                prjct:this.project,
                skl:[
                {
                skill_name:this.skill_name,
                skill_level:this.skill_level
                }
                ],
                sm:[
                {
                    platform:this.platform,
                    username:this.username,
                    social_URL:this.social_URL
                }
                ]
            }
            console.log(primaryDetails);
            await axios.put(`http://127.0.0.1:8000/get_individual_resume/${this.id}`,primaryDetails).then((res)=>{
            console.log(res.data)
            }).catch((err)=>{
            console.log(err);
            })
        },
        async formget(){
             await axios.get(`http://127.0.0.1:8000/get_individual_resume/${this.id}`).then((res)=>{
                  this.items=res.data
                  console.log(this.items, "<<<<<<<<<<<<<")
                  console.log("ok")
                  console.log('data:',res.data)
                  console.log("Items: ", this.items)
              })
              .catch(function(error){
                  console.log('error:',error)
              })
        },
        
        },

        async mounted() {
          await this.formget()
          console.log("id>>>>>>>>>>>>>>>>>test: ", this.items.prim)

          
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


</style>
