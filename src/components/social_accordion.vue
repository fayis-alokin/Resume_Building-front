<template>
    <v-row justify="center">
        <v-expansion-panels accordion focusable>
          <v-expansion-panel>
            <v-expansion-panel-header>Social Media Details</v-expansion-panel-header>
            <v-expansion-panel-content>
               <v-col v-for="(item,i) in social_ar" :key="i">
                  <v-row class="input">
                    <v-panel-title class="input-label">
                      Platform
                    </v-panel-title>
                    <v-text-field
                      v-model="item.platform"
                      :counter="10"
                      placeholder="Eg:- Instagram"
                      class="mr-6"
                    ></v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class="input-label">
                      Username
                    </v-panel-title>
                    <v-text-field
                      v-model="item.username"
                      placeholder="Username"
                      class="mr-6"
                    ></v-text-field>
                  </v-row>
                  <v-row class="input">
                    <v-panel-title class="input-label">
                      URL
                    </v-panel-title>
                    <v-text-field
                      v-model="item.social_URL"
                      placeholder="URL"
                      class="mr-6"
                    ></v-text-field>
                  </v-row>
                  <v-devider></v-devider>
                  <v-row>
                    <v-btn @click="addSocial" class="mb-3">Add more</v-btn>
                    <v-btn @click="removeSocial" class="mb-3 ml-3">Remove</v-btn>
                  </v-row>
                </v-col>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'SocialAccordion', 
    props:{
      social_details:Object
    }, 
    data: () => ({
    count:1,
    social:{
      platform:'',
      username:'',
      social_URL:''
    },
    social_ar:[
      {
        platform:'',
        username:'',
        social_URL:''
      }
    ]
  }),
  mounted(){
    if(this.social_details)
    this.social=this.social_details
   },
   methods:{
    addSocial() {
      this.social_ar.push({
        platform:'',
        username:'',
        social_URL:''
       })
    },
    removeSocial(index){
      this.removedsocial_ar.push(this.social_ar[index]?.id);
      this.social_ar.splice(index, 1);
      if (!this.social_ar.length) this.addSocial();
    }
   },
  watch:{
    social_ar:{
      handler(val){
        this.$emit('social',val)
      },
      deep:true
    }
  }   
}
</script>