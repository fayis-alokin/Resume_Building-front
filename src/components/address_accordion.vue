<template>
    <v-row justify="center">
        <v-expansion-panels accordion>
          <v-expansion-panel>
            <v-expansion-panel-header>Add Address Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-text-field
                  v-model="name"
                  :counter="10"
                  :rules="nameRules"
                  label=" House Name"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="Street"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="phone"
                  :rules="phoneRules"
                  label="City"
                  required
                ></v-text-field>
                <v-select
                  v-model="select"
                  :items="items"
                  label="Country"
                ></v-select>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'AddressAccordion',
    data: () => ({
    items: ['Japan', 'Uzbekisthan', 'America', 'India'],
  }),
}
</script>