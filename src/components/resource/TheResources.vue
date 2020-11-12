<template>
 <base-card>
    <base-button @click="setSelectedTab('learning-resources')" :mode='storedResButtonMode'>Learning resources</base-button>

    <base-button @click='setSelectedTab("add-resources")' :mode='addResButtonMode'> Add resources</base-button>
    <component :is='selectedTab'></component>
</base-card>
</template>

<script>
import LearningResources from './LearningResources.vue';
import AddResources from './AddResources.vue';

export default {
    components:{
         LearningResources,
         AddResources,
    },
    computed:{
        storedResButtonMode(){
           return  this.selectedTab === 'learning-resources'? null :"flat"
        },
         addResButtonMode(){
           return  this.selectedTab === 'add-resources'? null :"flat"
        },
    },
    data(){
     return {
        selectedTab:'learning-resources',
        storedResource:[
                {
                    id:'official-guide',
                    title:'Official VUE guide',
                    desc:'Official Vue framework documentation',
                    link:'https://vuejs.org/',
                },
                {
                    id:'google',
                    title:'Google',
                    desc:'Learn to google...',
                    link:'https://www.google.com/',
                },
                ],
     
    }
    },
    provide(){
       return { resources:this.storedResource,}
    },

    methods:{
        setSelectedTab(tab){
            this.selectedTab = tab;
        }
    },
    
}
</script>

<style  scoped>

</style>