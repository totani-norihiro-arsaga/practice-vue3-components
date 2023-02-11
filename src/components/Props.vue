<template>
  <h3 :class="$attrs.class">props</h3>
  <p >{{ props.message }}</p>
  <p>{{ props.other }}</p>
  <p>{{props.num + 100}}</p>
</template>

<script setup>
import {useAttrs} from "vue";

const props = defineProps({
    message:String,
    other:{
      type:String,
      default:'default値',
    },
    num:{
      type:Number,
      required:true,
    }
  })
const attrs = useAttrs();
console.log(attrs.class);
</script>

<style scoped>
.active{
  color:orange;
  font-weight: 900;
}

.primary{
  color:dodgerblue;
  font-weight: 900;
}

.forest{
  color:green;
  font-weight: 900;
}

</style>