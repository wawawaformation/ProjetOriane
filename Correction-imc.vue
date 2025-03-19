<template>
  <div class="content">
  <h1>Calcul IMC</h1>
  <form>
    <div class="field">
      <label for="weight">Poids (kg)</label>
      <input
        v-model="weight"  
        type="number" 
        id="weight" 
        name="weight" 
        min="20" 
        max="300" 
        required>
    </div>
    <div class="field">
      <label for="height">Taille (cm)</label>
      <input
        v-model="height" 
        type="number" 
        id="height" 
        name="height" 
        min="100" 
        max="250" 
        required>
    </div>
    <button @click.prevent="handleSubmit" type="submit">Calculer</button>
  </form>
</div>
<div v-if="Object.keys(msg) !== 0" :class="msg.class">{{ msg.text }}</div>
</template>


<script setup>
import { ref } from 'vue';

const weight = ref(0)
const height = ref(0)
const msg = ref({})


/**
 * Calcul IMC et edition du message msg.value avec les propriétés imc, text et class
 * @returns void
 */
const handleSubmit = ()=>{
  //imc = poids / taille² => taille en mètre ou on divise par 10000 si en cm
  let imc = weight.value / (height.value/100)**2
  imc = imc.toFixed(2)
 
  if(imc < 18.5){
    msg.value = {
      imc: imc,
      text: 'Insuffisance pondérale', 
      class: 'msg insufficient'
    }
  }else if(imc >= 18.5 && imc < 25){
    msg.value = {
      imc: imc,
      text: 'Corpulence normale', 
      class: 'msg normal'
    }
  }else if(imc >= 25 && imc < 30){  
    msg.value = {
      imc: imc,
      text: 'Surpoids', 
      class: 'msg overweight'
    }
  }else if(imc >= 30 && imc < 35){
    msg.value = {
      imc: imc,
      text: 'Obésité modérée', 
      class: 'msg moderate'
    }
  }else if(imc >= 35 && imc < 40){
    msg.value = {
      imc: imc,
      text: 'Obésité sévère', 
      class: 'msg severe'
    }
  }else{
    msg.value = {
      imc: imc,
      text: 'Obésité morbide', 
      class: 'msg morbid'
    }
  }
  console.log(msg.value)
}
</script>


<style scoped>
  

  .msg{
    /**/ 
    box-sizing: border-box;
    margin: 1rem;
    padding: 1rem;
    background-color: #fff;
    font-weight: bold;
    text-align: center;
    border-radius: 1rem;

  }

  .insufficient, .overweight{
    color: orange;
  }
  .normal{
    color: green;
  }
  .moderate, .severe{
    color: orangered;
  }
  .morbid{
    color: darkviolet;
  }

  

</style>