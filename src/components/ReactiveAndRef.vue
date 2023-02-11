<template>
  <p>ref count:{{ count }}</p>
  <p>reactive count:{{ state.count }}</p>
  <button @click="clickRef">ref countup</button>
  <button @click="clickReactive">reactive countup</button>
</template>

<script setup>
import {ref, reactive} from "vue";

const count = ref(0);
const state = reactive({
  count: 1,
});

const clickRef = ()=>{
  count.value++;
}
const clickReactive = () => {
  state.count++;
}

</script>

<style scoped>

</style>