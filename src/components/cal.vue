
<script setup>

import { round } from 'lodash';
import {ref} from 'vue'

let current = ref('')

let result = ref(0)

let click = false

function append(number) {
  current.value = current.value + number
}

function clear() {
    result.value = 0
    current.value = ''
    click = false
    }

function sign() {
    if(current.value === ''){
      current.value = '-'
    }
  }

function opration(func) {
  if (!current.value){
    return
  }
    if (!click){
      click = true
      result.value = parseFloat(current.value)
      current.value = ''
      return
    }
    result.value = func(result.value,parseFloat(current.value))
    current.value = ''
    return 
}


const add = (a,b) => a + b

const sub = (a,b) => a - b

const mul = (a,b) => a * b

const div = (a,b) => round(a / b, 2)

const mod = (a,b) => a % b

</script> 


<template>

    <n-space class="row" align="center" vertical >  
      <div class="cal">

        <n-space justify="space-between" item-style="font-size:50px;padding:20px 20px;">
          <div >{{ result }}</div>  
          <div >{{ current }}</div>  
        </n-space>

        <n-divider></n-divider>

        <n-space justify="space-around">
          <n-button @click="clear" class="button" strong secondary circle> C </n-button>
          <n-button @click="sign" class="button" strong secondary circle> +/- </n-button>
          <n-button @click="opration(mod)" class="button" strong secondary circle> % </n-button>
          <n-button @click="opration(div)" class="button" strong secondary circle> / </n-button>
        </n-space>
        <br>

        <n-space justify="space-around">
          <n-button @click="append('7')" class="button" strong secondary circle> 7 </n-button>
          <n-button @click="append('8')" class="button" strong secondary circle> 8 </n-button>
          <n-button @click="append('9')" class="button" strong secondary circle> 9 </n-button>
          <n-button @click="opration(mul)" class="button" strong secondary circle> X </n-button>
        </n-space>
        <br>

        <n-space justify="space-around">
          <n-button @click="append('4')" class="button" strong secondary circle> 4 </n-button>
          <n-button @click="append('5')" class="button" strong secondary circle> 5 </n-button>
          <n-button @click="append('6')" class="button" strong secondary circle> 6 </n-button>
          <n-button @click="opration(sub)" class="button" strong secondary circle> - </n-button>
        </n-space>
        <br>

        <n-space justify="space-around">
          <n-button @click="append('1')" class="button" strong secondary circle> 1 </n-button>
          <n-button @click="append('2')" class="button" strong secondary circle> 2 </n-button>
          <n-button @click="append('3')" class="button" strong secondary circle> 3 </n-button>
          <n-button @click="opration(add)" class="button" strong secondary circle> + </n-button>
        </n-space>
        <br>

        <n-space justify="space-around">
          <n-button @click="append('0')" class="button" strong secondary circle> 0 </n-button>
          <n-button @click="append('00')" class="button" strong secondary circle> 00 </n-button>
          <n-button @click="append('.')" class="button" strong secondary circle> . </n-button>
          <n-button  class="button" strong secondary circle> = </n-button>
        </n-space>
        <br>
      </div>
    </n-space>

  </template>
  
  <style scoped>
  .row {
    height: auto;
    background-color: rgb(234, 98, 98);
  }
  .cal {
    width: 450px;
    height: auto;
    background-color: rgb(138, 85, 85);
    margin: 50px;
    border-radius: 20px;
  }
  .button{
    width: 60px;
    height: 60px;
    font-size:25px;
    padding: 10px;
  }
  </style>