<template>
  <div class="home">
    <h1>Home</h1>
    <h2>Refs</h2>

    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne"> update Ninja one </button>

    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }}  - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo"> update Ninja two </button>



  </div>
</template>

<script>

import {ref,reactive} from 'vue';
// @ is an alias to /src

export default {
  name: 'HomeView',
  setup(){

    const ninjaOne = ref({name:'mario',age:23});
    
    const ninjaTwo = reactive({name:'contra',age:24})

    const nameOne = ref('')

    const updateNinjaOne = ()=>{
      ninjaOne.value.age = 40;
    }
    
    const updateNinjaTwo = ()=>{
      ninjaTwo.age = 29
    }

    return {ninjaOne,updateNinjaOne,ninjaTwo,updateNinjaTwo}


  },
 
}
</script>
