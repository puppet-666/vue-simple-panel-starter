<script lang="ts" setup>
defineProps({
  title: {
    type: String,
    default: '',
  },
  titleStyle: {
    type: Object,
    default: () => {},
  },
  isLong: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <div class="panel-block">
    <div
      class="panel-block-title"
      :class="[isLong ? 'panel-block-long-bg' : '']"
    >
      <div class="panel-block-title-logo" />
      <div
        class="panel-block-title-text"
        :style="titleStyle"
      >
        {{ title }}
      </div>
    </div>
    <div class="panel-block-chart">
      <slot />
    </div>
  </div>
</template>

<style scoped lang="scss">
.panel-block {
  margin-top: 16px;
  // margin-bottom: 20px;
}
.panel-block-title {
  position: relative;
  display: flex;
  height: 33px;
  align-items: center;

  background: url('@/assets/bg.png')  no-repeat 0 50% ;

  &-text {
    position: absolute;
    left: -6px;
    color: #eff5ff;
    font-size: 20px;
    text-indent: 2em;
  }
}

.panel-block-chart {
  margin-top: 16px;
}

.panel-block-long-bg {
  background: url('@/assets/bg-long.png')  no-repeat 0 50% ;
}
</style>
