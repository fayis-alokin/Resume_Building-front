<template>
    <v-row justify="center">
        <v-expansion-panels accordion focusable>
          <v-expansion-panel>
            <v-expansion-panel-header>Experience Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-col v-for="(item,i) in experience_ar" :key="i">
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      Job Role
                    </v-panel-title>
                    <v-text-field
                      v-model="item.role"
                      :counter="10"
                      placeholder="Add Role"
                      class="mr-6"
                      >
                    </v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      Name of the company
                    </v-panel-title>
                    <v-text-field
                      v-model="item.company_name"
                      placeholder="Add Company Name"
                      class="mr-6"
                      >
                    </v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      Location
                    </v-panel-title>
                    <v-text-field
                      v-model="item.location"
                      placeholder="Add Location"
                      class="mr-6"
                      >
                    </v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      Start Date
                    </v-panel-title>
                    <v-text-field
                      v-model="item.start_date"
                      placeholder="Add Start date"
                      class="mr-6"
                      >
                    </v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      End Date
                    </v-panel-title>
                    <v-text-field
                      v-model="item.end_date"
                      placeholder="Add End date">
                    </v-text-field>
                  </v-row>
                  <v-row>
                    <v-btn @click="addExperience" class="mb-3 ">Add more</v-btn>
                    <v-btn @click="count--" class="mb-3 ml-3">Remove</v-btn>
                  </v-row>
                </v-col>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'ExperienceAccordion',  
    props:{
      experience_details:Array
    },
    
    data: () => ({
    count:1,
    experience_ar:[
      {
        role:'',
        company_name:'',
        location:'',
        start_date:'',
        end_date:''
      }
    ]
  }),
  mounted(){
    if(this.experience_details)
    this.experience=this.experience_details
    this.experience_ar = JSON.parse(JSON.stringify(this.experience_details))
   },
   methods:{
    addExperience() {
      
      this.experience_ar.push({
        company_name:'',
        location:'',
        start_date:'',
        end_date:''
       
      
      })
             
    },
    removeSkill(index){
      this.removedskl_ar.push(this.skl_ar[index]?.id);
      this.skl_ar.splice(index, 1);
      if (!this.skl_ar.length) this.addSkill();
    }
   },
  watch:{
    experience_ar:{
      handler(val){
        console.log("dddddddddddd",val)
        this.$emit('experience',val)
      },
      deep:true
    }
  }
}
</script>

<style>
.row .input{
  margin: 0;
  
}
.input-label{
  width: 150px;
  padding-top: 20px;
  padding-right: 20px;
  margin-right: 20px;
  background-color: aliceblue;
}
</style>