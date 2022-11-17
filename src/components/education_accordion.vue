<template>
    <v-row justify="center">
        <v-expansion-panels accordion focusable>
          <v-expansion-panel>
            <v-expansion-panel-header>Education Details</v-expansion-panel-header>
            <v-expansion-panel-content>
               <v-col  v-for="(item,i) in education_ar"
               :key="i">
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Qualification
                  </v-panel-title>
                  <v-text-field
                    v-model="item.Qualification"
                    :counter="10"
                    placeholder="Add Qualification" class="mr-6">
                  </v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Course
                  </v-panel-title>
                  <v-text-field
                    v-model="item.Course_name"
                    placeholder="Add Course" class="mr-6">
                  </v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    University
                  </v-panel-title>
                  <v-text-field
                  v-model="item.University_name"
                  placeholder="Add University"
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Location
                  </v-panel-title>
                  <v-text-field
                    v-model="item.Location"
                    placeholder="Add Location"
                    class="mr-6"
                    >
                  </v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Passing year
                  </v-panel-title>
                  <v-text-field
                    v-model="item.passing_year"
                    placeholder="Add Passing Year"
                    class="mr-6"
                    >
                  </v-text-field>
                </v-row>
                <v-row class="">
                  <v-btn class="mb-3 " @click="addEducation">Add more</v-btn>
                  <v-btn class="mb-3 ml-3" @click="count--">Remove</v-btn>
                </v-row>
               </v-col>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>


export default{
    name : 'EducationAccordion',  
    props:{
      education_details:Array
    }, 
    data: () => ({
    count:1,
    
    education_ar:[
      {
        Qualification:'',
        Course_name:'',
        University_name:'',
        Location:'',
        passing_year:''
        
      }
      
    ]

    
  }),
   mounted(){
    if(this.education_details)
    this.education=this.education_details
    this.education_ar = JSON.parse(JSON.stringify(this.education_details))
    console.log("edu data>>>:",this.education_details, this.education_ar)
   },
   methods:{
    addEducation() {
      
      this.education_ar.push({
        Qualification:'',
        Course_name:'',
        University_name:'',
        Location:'',
        passing_year:''
       })
             
    },
    removeSkill(index){
      this.removedskl_ar.push(this.skl_ar[index]?.id);
      this.skl_ar.splice(index, 1);
      if (!this.skl_ar.length) this.addSkill();
    }
   },
  watch:{
    education_ar:{
      handler(val){
        console.log("cccccccccc",val)
        this.$emit('education',val)
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
.col{
  padding: 0px;
}
.addmore{
  margin-bottom: 10px;
}
</style>