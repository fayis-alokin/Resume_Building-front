<template>
    <v-btn @click="count++">
        Add More
    </v-btn>
</template>
<script>
export default{
    name: 'AddmoreBtn',
    data: () => ({
    count:1
  })
}
</script>