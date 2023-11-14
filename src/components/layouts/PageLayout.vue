<script lang="ts" setup>
const show = ref(false);

onMounted(() => {
  nextTick(() => {
    show.value = true;
  });
});
</script>

<template>
  <div class="panel-warp">
    <Transition name="left2right">
      <div
        v-if="show"
        class="panel-left"
      >
        <slot name="left" />
      </div>
    </Transition>
    <Transition name="right2left">
      <div
        v-if="show"
        class="panel-right"
      >
        <slot name="right" />
      </div>
    </Transition>
  </div>
</template>

<style scoped lang="scss">
.panel-warp {
  height: 100%;
}

.panel-left {
  position: fixed;
  z-index: 10;
  top: 0;
  left: 0;
  display: flex;
  width: 399px;
  height: 100%;
  box-sizing: border-box;
  flex-direction: column;
  padding-top: 95px;
  padding-right: 24px;
  padding-left: 24px;

  will-change: transform;
  &::after {
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, #040c1b 0%, rgba(4,12,27,0.15) 100%);
    content: "";
    filter: blur(4px);
  }
}

.panel-right {
  position: fixed;
  z-index: 10;
  top: 0;
  right: 0;
  display: flex;
  width: 399px;
  height: 100%;
  box-sizing: border-box;
  flex-direction: column;
  padding-top: 95px;
  padding-right: 24px;
  padding-left: 24px;
  will-change: transform;
  &::after {
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(-90deg, #040c1b 0%, rgba(4,12,27,0.15) 100%);
    content: "";
    filter: blur(4px);
  }
}

.left2right-enter-from,
.left2right-leave-to {
  transform: translateX(-100%);
}

.left2right-enter-to,
.left2right-leave-from {
  transform: translateX(0%);
}

.right2left-enter-from,
.right2left-leave-to {
  transform: translateX(100%);
}

.right2left-enter-to,
.right2left-leave-from {
  transform: translateX(0%);
}

.left2right-enter-active, .bottom2top-enter-active, .right2left-enter-active {
  transition: transform 1s cubic-bezier(0.34, 1.56, 0.64, 1);
  transition-delay: 0.3s;
}

.left2right-leave-active, .bottom2top-leave-active, .right2left-leave-active {
  transition: transform 0.3s linear;
}
</style>
