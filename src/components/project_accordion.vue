<template>
    <v-row justify="center">
        <v-expansion-panels accordion focusable>
          <v-expansion-panel>
            <v-expansion-panel-header>Project Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-col sm="12" v-for="(item,i) in project_ar" :key="i">
                  <v-row class="input">
                    <v-panel-title class="input-label">
                      Project Title
                    </v-panel-title>
                    <v-text-field
                      v-model="item.project_title"
                      :counter="10"
                      placeholder="Add Project title"
                      class="mr-6"
                    ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Project Description
                  </v-panel-title>
                <v-text-field
                  v-model="item.project_description"
                  placeholder="Add Project description"
                  class="mr-6"
                ></v-text-field>
                  </v-row>
                  <v-row>
                    <v-btn @click="addProject" class="mb-3">Add more</v-btn>
                    <v-btn @click="removeProject" class="mb-3 ml-3">Remove</v-btn>
                  </v-row>
                </v-col>
                
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'ProjectAccordion',
    props:{
      project_details:Array
    },
    data: () => ({
    count:1,
    project_ar:[
      {
        project_title:'',
        project_description:''
      }
    ],
    project:{
      project_title:'',
      project_description:''
    },

  }),
  mounted(){
    if(this.project_details)
    this.project=this.project_details
    this.project_ar = JSON.parse(JSON.stringify(this.project_details))
   },
  methods:{
    addProject() {
        this.project_ar.push({
        project_title: "",
        project_description: "",
        })
    },
    removeProject(index){
      this.removedproject_ar.push(this.project_ar[index]?.id);
      this.project_ar.splice(index, 1);
      if (!this.project_ar.length) this.addProject();
    }
  },
  watch:{
    project_ar:{
      deep: true,
      handler(val){
        console.log("eeeeeee",val)
        this.$emit('project',val)
      }
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