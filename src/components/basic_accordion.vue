<template>
    <v-row justify="center">
        <v-expansion-panels accordion v-model="panel" focusable>
          <v-expansion-panel expand>
            <v-expansion-panel-header>Primary Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-row class="input">
                 
                  <v-panel-title class = "input-label">
                    Name
                   </v-panel-title>
                
                  <v-text-field
                  v-model="primary.name"
                  :counter = "10"
                  :rules="nameRules"
                  regular
                  placeholder="Add Name"
                  required
                  class="mr-6"
                ></v-text-field>
        
                </v-row>
                <v-devider></v-devider>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Email
                   </v-panel-title>
                  <v-text-field
                  v-model="primary.email"
                  :rules="emailRules"
                  placeholder="Add e-mail"
                  required
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Phone
                   </v-panel-title>
                  <v-text-field
                  v-model="primary.phone"
                  :rules="phoneRules"
                  placeholder="Add Phone number"
                  required
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Image
                   </v-panel-title>
                  <v-text-field
                  v-model="primary.image"
                  placeholder="Add image URL"
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class="input-label">
                    Summary
                   </v-panel-title>
                  <v-textarea
                  v-model="primary.summary"
                  placeholder="Add Summary"
                  class="mr-6"
                ></v-textarea>
                </v-row>
        
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-row>
</template>

<script>
export default{
    name : 'BasicAccordion',
    props:{
      primary_details:Object
    },
    data(){
    return{
      panel:0,
      primary:{
        name: '',
        email:'',
        phone:'',
        image:'',
        summary:''
      },
      nameRules: [
      v => !!v || 'Name is required',
      v => (v && v.length > 3) || 'Name must be greater than 3 characters',
      ],
    emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
      phoneRules: [
        v => !!v || 'Phone no. is required',
        v => /^\(?(\d{3})\)?[- ]?(\d{3})[- ]?(\d{4})$/.test(v) || 'Enter valid phone no.'
      ],


    }
   },
   mounted(){
    if(this.primary_details){
      console.log("Im basic")
    this.primary=this.primary_details
    }
    
   },
   watch:{
    primary:{
      handler(val){
        console.log("aaaaaaaaaaaaaaaaaaa",val)
        this.$emit('primary',val)
      },
      deep:true
    }
  }
  //  },
  //  methods: {
  //   capitalletter(){
  //     if(this.basic.name[0].toLowerCase())
  //       this.basic.name=this.basic.name[0].toUpperCase()+this.basic.name.slice(1)
  //   }
  // }

    
}

</script>

<style>
.row .input{
  margin: 0;
  
}
.input-label{
  width: 100px;
  padding-top: 20px;
  padding-right: 20px;
  margin-right: 20px;
  background-color: aliceblue;
}
.v-expansion-panel-content__wrap{
  padding: 0px;
}


</style>