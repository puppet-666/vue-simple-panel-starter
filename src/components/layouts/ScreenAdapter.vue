<script lang="ts" setup>
import { useDebounceFn } from '@vueuse/core';

const props = withDefaults(defineProps<{
  width: number
  height: number
}>(), {
  width: 1920,
  height: 1080,
});

const style = reactive({
  width: `${props.width}px`,
  height: `${props.height}px`,
  transform: 'scale(1) translate(-50%, -50%)',
});

function getScale() {
  const w = window.innerWidth / props.width;
  const h = window.innerHeight / props.height;
  return w < h ? w : h;
}

function setScale() {
  const scale = getScale();
  style.transform = `scale(${scale}) translate(-50%, -50%)`;
}

onMounted(() => {
  setScale();
  window.onresize = useDebounceFn(() => {
    setScale();
  }, 1000);
});
</script>

<template>
  <div
    class="ScreenAdapter"
    :style="style"
  >
    <slot />
  </div>
</template>

<style lang="scss" scoped>
.ScreenAdapter {
  position: absolute;
  z-index: 6;
  top: 50%;
  left: 50%;
  overflow: hidden;
  // pointer-events: none;
  transform-origin: 0 0;
  transition: 0.3s;
}
</style>

