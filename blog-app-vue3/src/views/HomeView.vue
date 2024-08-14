<template>
  <div class="home">
    <h1>Home</h1>

    <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      {{ name }}

    </div>









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

import {ref,reactive,computed} from 'vue';
// @ is an alias to /src

export default {
  name: 'HomeView',
  setup(){

  //_____computed values___________________
  const search= ref('');
  const names = ref(['mario','yoshi','luigi','bowser','koopa','peach'])

  const matchingNames = computed(()=>{
    return names.value.filter((name)=> name.includes(search.value))
  })

  return {names,search,matchingNames}

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
 
}
</script>
