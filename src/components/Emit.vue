<template>
  <p>{{ props.message }}</p>
  <button @click="$emit('doEmit')">emitさせるよ</button>
  <div>
    <input type="text" v-model="argMessage" @input="doDoEmit"/>
  </div>
</template>

<script setup>
import { ref } from "vue";
const props = defineProps({
  message: {
    type: String,
    required: true,
  },
});
const abc = defineEmits({
  doDo: (argMessage)=>{
    return true;
  }

});
const doDoEmit = () => {
  abc("doDo",argMessage);
};
let argMessage = ref("message");
</script>

<style scoped></style>
