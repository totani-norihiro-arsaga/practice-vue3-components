<script setup>
import { inject } from 'vue';

const provideMessage = inject('provideMessage');
</script>
<template>
    <div>{{ provideMessage }}</div>
</template>