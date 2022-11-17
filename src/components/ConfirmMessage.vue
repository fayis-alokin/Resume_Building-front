<!-- <template>
    <v-row justify="center">
      <v-dialog
        v-model="dialog"
        persistent
        max-width="290"
      >
        <template>
      </template>
      <v-card>
        <v-card-title class="text-h5">
          Delete Entry
        </v-card-title>
        <v-card-text>Do you want to delete?</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green darken-1"
            text
            @click="$emit('delete-id')"
          >
            Yes
          </v-btn>
          <v-btn
            color="green darken-1"
            text
            @click= "dialog = false"
          >
            No
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
  export default {
    name:"DeleteMessage",
    props:{
        dialog: Boolean
    }
  }


</script> -->