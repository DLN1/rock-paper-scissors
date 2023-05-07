<template>
  <div class='outerContainer'>
    <div @click='$emit("optionPicked", option)' :style="{'border-color': option.color}" class="handContainer">
      <img :alt='option.name + " option"' :src="option.icon" />
    </div>
  </div>
</template>

<script setup>
import { defineProps, toRefs } from "vue";

const props = defineProps({ option: Object });

const { option } = toRefs(props);
</script>

<style scoped>
.handContainer {
  background: white;
  border-radius: 50%;
  width: 26vmin;
  height: 26vmin;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 10px solid;
}

.handContainer:hover {
    cursor: pointer;
    outline: 20px solid rgba(255, 255, 255, 0.069);
    transform: rotate(25deg);
}



@media (min-width: 768px) {
  .handContainer > img {
    width: 56%;
  }
}
</style>
