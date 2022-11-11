<template>
   <v-main>
    <ListingTable/>
   </v-main>

</template>

<script>
import ListingTable from '../components/listing_page.vue'

export default{
    name :'HomePage',
    components:{
        ListingTable
    }
}
</script>