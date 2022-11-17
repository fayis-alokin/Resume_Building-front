<template>
    <v-row justify="center">
        <v-expansion-panels accordion focusable> 
          <v-expansion-panel>
            <v-expansion-panel-header>Address Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-row class="input">
                  <v-panel-title class = "input-label">
                    House Name
                   </v-panel-title>
                  <v-text-field
                  v-model="address.House_name"
                  :counter="10"
                  placeholder=" Add House Name"
                  required
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class = "input-label">
                    Street
                   </v-panel-title>
                  <v-text-field
                  v-model="address.Street"
                  placeholder="Add Street"
                  required
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class = "input-label">
                    City
                   </v-panel-title>
                  <v-text-field
                  v-model="address.City"
                  placeholder="Add City"
                  required
                  class="mr-6"
                ></v-text-field>
                </v-row>
                <v-row class="input">
                  <v-panel-title class = "input-label">
                    Pin Code
                   </v-panel-title>
                  <v-text-field
                  v-model="address.pincode"
                  placeholder="Add Pincode"
                  required
                  class="mr-6"
                ></v-text-field>
                </v-row>
               <v-row class="input">
                <v-panel-title class = "input-label">
                  Country
                 </v-panel-title>
                <v-select
                v-model="address.Country"
                :items="items"
                placeholder="Select your country"
                class="mr-6"
              ></v-select>
               </v-row>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'AddressAccordion',
    props:{
      address_details:Object
    },
    data: () => ({
    items: ['Japan', 'Wakanda', 'USA', 'India','Nigeria','Germany','Brazil','Australia'],
    address:{
      House_name:'',
      Street:'',
      City:'',
      pincode:'',
      Country:''
    }
  }),
  mounted(){
    if(this.address_details)
    this.address=this.address_details
   },
  watch:{
    address:{
      handler(val){
        console.log("bbbbbbbbbbbbbbbbb",val)
        this.$emit('address',val)
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