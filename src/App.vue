<script setup>
import {ref} from "vue";
import Hello from "./components/Hello.vue";
import ReactiveAndRef from "./components/ReactiveAndRef.vue";
import Props from "./components/Props.vue";
import Emit from "./components/Emit.vue";

let message = ref('子コンポーネントで値を変えてはいけません。');

function changeMessage() {
  message.value = '親コンポーネントで値を変えましたよ。'
}
function addMessage(add) {
  console.log(add);
  message.value+=add.name;
}

</script>

<template>
  <h1>vue3入門</h1>
  <h2>コンポーネントの再利用</h2>
  <Hello />
  <Hello />
  <Hello />
  <h2>reactive ref</h2>
  <ReactiveAndRef/>
  <h2>コンポーネントの独立</h2>
  <ReactiveAndRef/>
  <h2>propsで親から子へ値渡し</h2>
  <Props class="forest" message="App.vueからの値です" other="二つ目の値" num="1000"/>
  <Props class="active" message="別の値を渡しています。" :num="1000"/>
  <h2>emitで子から親へイベント通知</h2>
  <Emit :message="message" @doEmit="changeMessage" @doDo="addMessage"/>
</template>

<style scoped>

</style>
