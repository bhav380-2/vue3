<template>

    <div class="post-list">
        <div v-for="post in posts" :key="post.id">

            <SinglePost :post="post"/>
        </div>


    </div>


</template>


<script>

import { onMounted } from 'vue';
import SinglePost from './SinglePost.vue';
import { onUnmounted } from 'vue';
import { onUpdated } from 'vue';


export default{

    props: ['posts'],
    components :{
        SinglePost : SinglePost
    },

    setup(props){

        onMounted(()=>{
            console.log('components mounted');
            
        })

        onUnmounted(()=>{

            console.log("component unmounted")

        })

        onUpdated(()=>{
            console.log("component updated");

        })






    }



}





</script>

<style>


</style>