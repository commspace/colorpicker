<template>
  <p>{{ currentColor }}</p>
  <ColorPicker
    ref="colorPickerRef"
    style="margin: 50px"
    mode="solid"
    :degree="45"
    :color="color"
    :gradients="gradients"
    @colorChanged="changed"
  />
</template>

<script setup>
import ColorPicker from "../components/ColorPicker.vue";
import { ref, computed } from "vue";

const currentColor = ref({ color: { r: 17, g: 75, b: 138, a: 1 } });

const mode = computed(() => currentColor.value.mode || "solid");
const color = computed(
  () => currentColor.value.color || { r: 17, g: 75, b: 138, a: 1 }
);
//17,75,138
const gradients = computed(() =>
  mode.value == "solid"
    ? [
        { percent: 0, color: color.value },
        { percent: 100, color: { r: 255, g: 255, b: 255, a: 1 } },
      ]
    : currentColor.value.color
);
const colorPickerRef = ref(null);
function changed(color) {
  currentColor.value = color;
}
</script>
