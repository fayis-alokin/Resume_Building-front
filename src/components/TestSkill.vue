<!-- <template>
    <div
    v-for="(item, index) in socialMediaItems"
              :key="index"
              class="form-group">
              <v-row>
                <v-col
                  cols="5"
                  sm="5"
                  md="5"
                  lg="5"
                  class="pl-0 ml-0 mt-0 pt-0 pb-2"
                >
                  <v-divider />
                  <hb-twin-selection title="Social Media">
                    <v-select
                      v-model="item.type"
                      class="socialmedia-options"
                      placeholder="Select Social Media Type"
                      single-line
                      :items="socialMediaOptions"
                      item-text="text"
                      item-value="value"
                      dense
                      solo
                      flat
                      hide-details="auto"
                      attach
                      :rules="isValidType(item)"
                    >
                      />
                    </v-select>
                  </hb-twin-selection>
                  <v-divider />
                </v-col>
          
                <v-col
                  cols="7"
                  class="pr-0 ml-0 mt-0 pt-0 pb-2 social-media-details"
                >
                  <div class="social-media-url">
                    <v-divider />
                    <hb-twin-selection title="Social Media URL">
                      <v-text-field
                        v-model="item.url"
                        placeholder="Enter Social Media URL"
                        single-line
                        dense
                        solo
                        flat
                        hide-details="auto"
                        :rules="isValidURL(item) ? rules.urlRules : []"
                      />
                    </hb-twin-selection>
                    <v-divider />
                  </div>
                  <div>
                    <div
                      @click="removeSocialMedia(index)"
                    >
                      <hb-icon
                        class="hand"
                      >
                        mdi-close
                      </hb-icon>
                    </div>
                  </div>
                </v-col>
                <div
                  v-if="isLastItem(index)"
                  class="align-right"
                >
                  <v-layout class="hand mb-4 pt-2">
                    <hb-link @click="addSocialMedia">
                      + Add Additional Social Media
                    </hb-link>
                  </v-layout>
                </div>
              </v-row>
            </div>
</template>

<script>
export default{
    name:'SkillTest',
    data() {
        return {
            socialMediaItems:[],
            item:{
                type:'',
                url:''
            }
        }
    },
    methods:{
        addSocialMedia() {
        this.socialMediaItems.push({
        type: "",
        url: "",
        is_active: true,
      });
    },
    removeSocialMedia(index) {
      this.removedSocialMediaList.push(this.socialMediaItems[index]?.id);
      this.socialMediaItems.splice(index, 1);
      if (!this.socialMediaItems.length) this.addSocialMedia();
    }
    }
}
</script> -->