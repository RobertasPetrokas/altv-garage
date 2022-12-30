<template>
  <div class="p-bold border-default tag">{{ text }}</div>
</template>

<script>
export default {
  name: "tag",
  props: { text: String },
};
</script>

<style scoped>
.tag {
  padding: 0.9vh 0.8vw;
  margin: auto;
  white-space: nowrap;
}
</style>
