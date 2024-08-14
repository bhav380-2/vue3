<template>
  <div class="home">
    <p ref="para"> My name is {{ name }} and my age is {{ 22 }}</p>
    <button @click="handleClick"> click me</button>
  </div>
</template>

<script>

import {ref} from 'vue';
// @ is an alias to /src

export default {
  name: 'HomeView',
  setup(){

    console.log('setup')
    let name = 'mario';
    let age = 30;

    const para = ref(null);

    const handleClick = ()=>{
      console.log(para,para.value)
      para.value.classList.add('test');
      para.value.textContent= "hello, ninjas"
    }


    return {
      name:name,
      age: age,
      handleClick,
      para
      
    }

  },
 
}
</script>
