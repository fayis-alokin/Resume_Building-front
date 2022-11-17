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
    <EducationAccordion v-if="items.edu" :education_details="items.edu[0]" @education="getEducationDetails"/>
    <ExperienceAccordion v-if="items.exp" :experience_details="items.exp[0]" @experience="getExperienceDetails"/>
    <ProjectAccordion v-if="items.prjct" :project_details="items.prjct[0]" @project="getProjectDetails"/>
    <SkillAccordion v-if="items.skl" :skill_details="items.skl[0]" @skill="getSkillDetails"/>
    <SocialAccordion v-if="items.sm" :social_details="items.sm[0]" @social="getSocialDetails"/>
    <v-row>
      <v-btn class="mb-5 teal" @click="edit_resume">
        Edit
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
// import axios from 'axios'
export default{
    name:'ResumeUpdate',
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
}
</script>