<template>
    <v-row justify="center">
        <v-expansion-panels accordion focusable>
          <v-expansion-panel>
            <v-expansion-panel-header>Skill Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-col v-for="(item, index) in skl_ar"
                :key="index">
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      Skill Name
                    </v-panel-title>
                    <v-text-field
                      v-model="item.skill_name"
                      :counter="10"
                      placeholder="Add Skill Name"
                      class="mr-6"
                      >
                    </v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class = "input-label">
                      Skill level
                    </v-panel-title>
                    <v-select
                    v-model="item.skill_level"
                    :items="items"
                    placeholder="Skill level"
                    class="mr-6"
                  ></v-select>
                  </v-row>
                  <v-row>
                    <v-btn @click="addSkill" class="mb-3 ">Add more</v-btn>
                    <v-btn @click="removeSkill" class="mb-3 ml-3">Remove</v-btn>
                  </v-row>
                </v-col>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'SkillAccordion',
    props:{
      skill_details:Object
    },
    data: () => ({
    items: ['Beginner', 'Intermediate', 'Expert'],
    
    skl_ar:[
      {
        skill_name:'',
        skill_level:''
      }
    ],
    skill:{
      skill_name:'',
      skill_level:''
    }
  }),
  mounted(){
    if(this.skill_details)
    this.skill=this.skill_details
   },
   methods:{
    addSkill() {
      
      this.skl_ar.push({
        skill_name: "",
        skill_level: "",
       
      
      })
             
    },
    removeSkill(index){
      this.removedskl_ar.push(this.skl_ar[index]?.id);
      this.skl_ar.splice(index, 1);
      if (!this.skl_ar.length) this.addSkill();
    }
   },
  watch:{
    skl_ar:{
      handler(val){
        this.$emit('skill',val)
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
  width: 200px;
  padding-top: 20px;
  padding-right: 20px;
  margin-right: 20px;
  background-color: aliceblue;
}
</style>