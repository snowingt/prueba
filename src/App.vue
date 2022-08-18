<script setup>
import { ref } from "@vue/reactivity"
import { computed } from "@vue/runtime-core"
let color=["red",'blue','yellow']
let arrayNumber= ref([])
let count= ref(0)               
const increment=()=>{
  count.value ++
 
  
}
const decrement=()=>{
  count.value --
 
  
}
const resect=()=>{
  count.value =0
 
  
}
let add =()=>{
  arrayNumber.value.push(count.value)
  console.log(arrayNumber)
}
const block= computed(()=>{
  const numSearch=arrayNumber.value.find((num) =>num ===count.value)
  console.log(numSearch)
  if(numSearch===0){
    return true
  }
  return numSearch? true:false;
})


    
</script>

<template>
<h2 v-if="count >0" :style="{color:color[1]}"

>{{count}}</h2>
<h2 v-else-if="count==0" :style="{color:color[2]}">{{count}}</h2>
<h2 v-else :style="{color:color[0]}">{{count}}</h2>

<button @click="increment">count +:</button>
<br/>
<button @click="decrement">decrement -:</button>
<br/>
<button @click="resect">count resect:</button>
<br/>
<button @click="add" :disabled="block">add</button>
<ul>
  <li v-for="(number,index) in arrayNumber" :key="index"
   >{{number}}</li>
</ul>
  
</template>
<style scope>
h1{
  color:red
}

</style>