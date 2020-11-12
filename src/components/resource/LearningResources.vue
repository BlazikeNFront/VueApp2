<template>
        <single-resource v-for='res in resources' :key='res.id' :desc='res.desc' :title='res.title' :link="res.link"></single-resource>
</template>


<script>
import SingleResource from './SingleResource.vue';



export default {
    components:{
        SingleResource,
      
    },
  inject:{
      resources:['resources']
  }
    
}
</script>
<style scoped>

</style>