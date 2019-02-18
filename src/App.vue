<template>
  <div id="app">

    <Conversor class="item" moeda-a="USD" moeda-b="BRL"/>
    <Conversor class="item" moeda-a="USD" moeda-b="BRL"/>
    <Conversor class="item" moeda-a="USD" moeda-b="BRL"/>

    <Conversor class="item" moeda-a="USD" moeda-b="BRL"/>
    <Conversor class="item" moeda-a="USD" moeda-b="BRL"/>
    <Conversor class="item" moeda-a="USD" moeda-b="BRL"/>

  </div>
</template>

<script>

import Conversor from "./components/Conversor"

export default {
  name: 'app',
  components: {
    Conversor
  }
}
</script>

<style>
#app {
   color: #fff; 
   text-align: center;   
}

.item {
    display: inline-block;
    width: 25%;
    height: 150px;
    margin-left: 10px;  
    margin-top: 20px; 
}

</style>
