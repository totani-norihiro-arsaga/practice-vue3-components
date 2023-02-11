<template>
  <p>{{props.message}}</p>
  <button @click="$emit('doEmit')" >emitさせるよ</button>
  <button @click="doDoEmit" >doDoEmitさせるよ</button>
</template>

<script setup>
const props = defineProps({
  message:{
    type:String,
    required:true,
  }
});
const abc = defineEmits(['doDo','doEmit']);
const doDoEmit = ()=>{
  abc('doEmit');
  abc("doDo",{
    name:'ikko',
    form:'fukuoka',
    age:'over60',
  });
}
</script>

<style scoped>

</style>