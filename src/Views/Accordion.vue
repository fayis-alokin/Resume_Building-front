
<template>
  <v-main>
    <FormHeading></FormHeading>
    <SubHeading/>
    <v-form
    ref="form"
    v-model="valid"
    lazy-validation
    >
    <BasicAccordion/>
    <AddressAccordion/>
    <EducationAccordion/>
    <ExperienceAccordion/>
    <ProjectAccordion/>
    <SkillAccordion/>
    <SocialAccordion/>
    <ButtonS/>
  </v-form>
    
  </v-main> 
  
  

</template>

<script>
import FormHeading from '../components/formheadings.vue'
import SubHeading from '../components/accordiontitle.vue'
import BasicAccordion from '../components/basic_accordion.vue'
import AddressAccordion from '../components/address_accordion.vue'
import EducationAccordion from '../components/education_accordion.vue'
import ExperienceAccordion from '../components/experience_accordion.vue'
import ProjectAccordion from '../components/project_accordion.vue'
import SkillAccordion from '../components/skill_accordion.vue'
import SocialAccordion from '../components/social_accordion.vue'
import ButtonS from '../components/Buttons.vue'
  export default {
    name: 'accordionForm',

    components:{
      FormHeading,
      SubHeading,
      BasicAccordion,
      AddressAccordion,
      EducationAccordion,
      ExperienceAccordion,
      ProjectAccordion,
      SkillAccordion,
      SocialAccordion,
      ButtonS
      
    },

    data: () => ({
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader',
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify',
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify',
        },
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com',
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com',
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuejs.com/vuetify',
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs',
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify',
        },
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
    }),
  }
</script>

<style>
.row{
  padding: 10px;
  margin-top: 20px;
}
</style>
