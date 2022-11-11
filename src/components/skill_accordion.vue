<template>
    <v-row justify="center">
        <v-expansion-panels accordion>
          <v-expansion-panel>
            <v-expansion-panel-header>Add Skill Details</v-expansion-panel-header>
            <v-expansion-panel-content>
                <v-text-field
                  v-model="name"
                  :counter="10"
                  :rules="nameRules"
                  label="Skill Name"
                ></v-text-field>
                <v-select
                  v-model="select"
                  :items="items"
                  label="Skill level"
                ></v-select>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
    </v-row>
</template>
<script>
export default{
    name : 'SkillAccordion',
    data: () => ({
    items: ['Beginner', 'Intermediate', 'Expert'],
  }), 
}
</script>