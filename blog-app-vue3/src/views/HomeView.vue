<template>
  <div class="home">
    <h1>Home</h1>

    <div v-if="error">{{ error }}</div>
    <PostList  v-if="posts.length"  :posts="posts" />
    <div v-else>Loading...</div>

    <button @click="showPosts=!showPosts"> toggle Posts</button>
    <button @click="posts.pop()">delete a posts</button>


    <!-- <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      {{ name }}

    </div>

    <button @click="handleClick" type="button">Stop Watching</button>

 -->







    <!-- ______ref v/s reactive_______________ -->
    <!-- <h2>Refs</h2> -->
    <!-- <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne"> update Ninja one </button>

    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }}  - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo"> update Ninja two </button>

 -->

  </div>
</template>

<script>

import PostList from '../components/PostList.vue'

import { watch, watchEffect } from 'vue';
import { ref, reactive, computed } from 'vue';
// @ is an alias to /src

export default {
  name: 'HomeView',

  components : {PostList},

  setup() {
    const posts = ref([]);
    const error = ref(null)

    const load = async()=>{
      try{

        let data = await fetch('http://localhost:3000/posts')

        if(!data.ok){
          throw Error('no data available');
        }

        posts.value = await data.json();

      }catch(err){
        error.value = err.message;
        console.log(error.value);

      }
    }

    load();

    const showPosts = ref(true);
    return { posts ,showPosts,error};
  }








  // setup() {

  //   //_____computed values___________________
  //   const search = ref('');
  //   const names = ref(['mario', 'yoshi', 'luigi', 'bowser', 'koopa', 'peach'])

  //   const stopWatch = watch(search,()=>{
  //     console.log("watch function search run")
  //   })

  //   const stopEffect = watchEffect(()=>{
  //     console.log('watchEffect function ran',search.value)
  //   })

  //   const matchingNames = computed(() => {
  //     return names.value.filter((name) => name.includes(search.value))
  //   })

  //   const handleClick = ()=>{

  //     stopWatch();
  //     stopEffect();

  //   }
  // return { names, search, matchingNames, handleClick }
// }

  

  //______ref v/s reactive_______________
  // const ninjaOne = ref({name:'mario',age:23});
  // const ninjaTwo = reactive({name:'contra',age:24})
  // const nameOne = ref('')

  // const updateNinjaOne = ()=>{
  //   ninjaOne.value.age = 40;
  // }

  // const updateNinjaTwo = ()=>{
  //   ninjaTwo.age = 29
  // }
  // return {ninjaOne,updateNinjaOne,ninjaTwo,updateNinjaTwo}


}


</script>
