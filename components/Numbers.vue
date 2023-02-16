
<template>
  
  <div class="number" @click="$emit('buttonWasClicked', number)">
        {{ number.value }}
  </div>

</template>

<script setup >

defineProps(['number'])

</script>

<style>

</style>