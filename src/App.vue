<script setup>
import {ref, computed, provide} from "vue";
import Hello from "./components/Hello.vue";
import ReactiveAndRef from "./components/ReactiveAndRef.vue";
import Props from "./components/Props.vue";
import Emit from "./components/Emit.vue";
import User from "./components/User.vue";
import Tokyo from "./components/Tokyo.vue";
import Kyoto from "./components/Kyoto.vue";
import Child from "./components/Child.vue";

let message = ref('子コンポーネントで値を変えてはいけません。');

function changeMessage() {
  message.value = '親コンポーネントで値を変えましたよ。'
}
function addMessage(argMessage) {
  message.value = argMessage;
}

let city = ref('tokyo');

const tabs = {
  tokyo: Tokyo,
  kyoto: Kyoto,
}
let tab = computed(() => tabs[city.value]);

let provideMessage = ref('親コンポーネントからやってきた');

provide('provideMessage',provideMessage);

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

  <h2>slotを使用する</h2>
  <User>
    <template #title="{message}">
      <h1 style="color: orange; font-weight: 900; font-size: 1.4em">ユーザー情報</h1>
      <h3>{{ message }}</h3>
    </template>
    <template #contents="{message}">
      <div>john doe</div>
      <div>john doe</div>
      <div>{{ message }}</div>
    </template>
    <template #action><button>ユーザー追加</button></template>
    <span>defaultです</span>
  </User>

  <h2>Dynamitコンポーネント</h2>
  <keep-alive>
    <component :is="tab"></component>
  </keep-alive>
  <button @click="city='tokyo'">tokyo</button>
  <button @click="city='kyoto'">kyoto</button>

  <h2>provideとinject</h2>
  <Child></Child>
  <input type="text" v-model="provideMessage">
</template>

<style scoped>
h2{
  margin-top: 50px;
}
</style>
