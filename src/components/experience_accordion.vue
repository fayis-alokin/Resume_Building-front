<template>
    <v-row justify="center">
        <v-expansion-panels accordion>
          <v-expansion-panel>
            <v-expansion-panel-header>Add Experience Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-text-field
                  v-model="name"
                  :counter="10"
                  :rules="nameRules"
                  label=" Role"
                  
                ></v-text-field>
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="Company Name"
                
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="Start date"
                  
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="End date"
                  
                ></v-text-field>
                
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'ExperienceAccordion',   
}
</script>