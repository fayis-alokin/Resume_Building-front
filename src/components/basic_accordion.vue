<template>
    <v-row justify="center">
    
        <v-expansion-panels accordion>
          <v-expansion-panel>
            <v-expansion-panel-header>Add Primary Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-text-field
                  v-model="name"
                  :counter="10"
                  :rules="nameRules"
                  label="Name"
                  required
                ></v-text-field>
            
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="Phone"
                  required
                ></v-text-field>
              
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-row>
</template>

<script>
export default{
    name : 'BasicAccordion',
    
}

</script>