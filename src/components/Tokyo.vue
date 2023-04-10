<script setup>
import {ref} from 'vue';
let count = ref(0);
const addCount = ()=>{
    count.value++
}
</script>
<template>
    <div>
        <h3>東京</h3>
        <p>日本の首都です。</p>
        <p>{{ count }}</p>
        <button @click="addCount" >addAount</button>
    </div>
</template>