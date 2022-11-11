<template>
    <v-row justify="center">
        <v-expansion-panels accordion>
          <v-expansion-panel>
            <v-expansion-panel-header>Add Education Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-text-field
                  v-model="name"
                  :counter="10"
                  :rules="nameRules"
                  label=" Qualification"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="Course"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="University"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="Location"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="Passing Year"
                  required
                ></v-text-field>
                
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'EducationAccordion',   
}
</script>