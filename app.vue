<template>
  <div class="calculator">
    <div>
      <h1 class="calc">Kalkulacka</h1>
      <div>
        <input placeholder=""  v-model="number1"/>
        <input placeholder=""  v-model="number2"/>
        <input placeholder=""  v-model="result"/>
      </div>
      
    </div>
    <div class="numbers">
        <button v-for="number of numbers" v-bind:key="number" :class="number">
        <Numbers v-bind:number="number" @buttonWasClicked="calOperation"> 
        
        </Numbers>
        
        </button>
    </div>
    
    <div class="operators">
      <button v-on:click="executePlus()">+</button>
      <button v-on:click="executeMinus()">-</button>
    </div>
    <div class="operators">
      <button v-on:click="executeEquals()">=</button>
    </div>
    
      
  </div>
</template>

<script setup>


const number1 = ref("");
const number2 = ref("");
const result = ref(0);
const plus = ref(false);
const minus = ref(false);

const executePlus=()=>{
  plus.value = true
}
const executeMinus=()=>{
  minus.value = true  
}
const executeEquals=()=>{
  if (minus.value == true){
    result.value = +number1.value - +number2.value
  }else if (plus.value == true) {
    result.value = +number1.value + +number2.value
  }
  
}


const numbers = ref([
  {value: "7"},
  {value: "8"},
  {value: "9"},
  {value: "6"},
  {value: "5"},
  {value: "4"},
  {value: "3"},
  {value: "2"},
  {value: "1"},
  {value: "0"}

])

function calOperation (number){
  let selectedNumber = numbers.value.find(item => item == number)
  if (plus.value == true || minus.value == true){
    number2.value += selectedNumber.value
  }else{
    number1.value += selectedNumber.value
  }
}

</script>



<style>

.operators{
  
  color:white;
  font-size: 20px;
  margin-left: 2px;
  margin-right: 2px;
  
}

.input-container{
  display: flex;
  align-items: center;
  width: 100%;
  max-height: 50px;
  
}

body{
  
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;

}

.calculator{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 100px;
  padding-bottom: 300px;
  max-width: 450px;
  background-color: #3b00001d;
  border-radius: 5px;
  margin: auto;


}

.calc {
  font-family: 'Orbitron', sans-serif;
  text-align: center;
  color:#100e0e;
}

input{
  
  display: center;
  justify-content: center;
  align-items: center;
  row-gap: 10px;
  font-family: 'Orbitron', sans-serif;
  background-color: #3e3d3f;
  color: white;
  border: solid rgb(255, 255, 255) 0.5px;
  max-width: 90px;
  border-radius: 5px;
  height: 50px;
  font-size: 18px;
  margin-bottom: 5px;
  text-align: center;

}

button {
  
  display: center;
  padding: 15px;
  margin: 5px;
  font-size: 20px;
  background-color: #a6a6a6;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
  
}

.buttons{
  
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  justify-content: space-between;
  height: 10px;
}


</style>