<template>
  <svg class="circle" width="38" viewBox="0 0 20 20">
    <circle class="bg" cx="10" cy="10" r="8" />
    <circle
      class="progress"
      cx="10"
      cy="10"
      r="8"
      :style="{ 'stroke-dashoffset': -51 - (51 / 100) * percentage }"
    />
    <img src="../assets/icons/engine-icon.svg" />
  </svg>
</template>
<style scoped>
.circle > .bg {
  stroke: rgba(255, 255, 255, 0.1);
  stroke-width: 2;
  fill: none;
}

.circle > .progress {
  fill: none;
  stroke: #c1ff3d;
  stroke-width: 2;
  stroke-dasharray: 51 51;
}
</style>
<script>
export default {
  name: "cycle_stats",
  props: ["percentage"],
};
</script>
