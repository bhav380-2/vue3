<template>
  <div class="home">
    <p ref="para"> My name is {{ name }} and my age is {{ age}}</p>
    <button @click="handleClick"> click me</button>
    <button @click="age++"> add 1 to age</button><br><br>

    <input type="text" v-model="name">

  </div>
</template>

<script>

import {ref} from 'vue';
// @ is an alias to /src

export default {
  name: 'HomeView',
  setup(){

    // console.log('setup')
    const name = ref('mario');
    const age = ref(22);

    const para = ref(null);

    const handleClick = ()=>{
      // console.log(para,para.value)
      // para.value.classList.add('test');
      // para.value.textContent= "hello, ninjas"
      age.value= 23;
      name.value='mariomario';
  
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
