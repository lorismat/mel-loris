<template>
  <div 
  :style="{ padding: `${paddingY} 0px` }"
  >
    <p>{{ title }}</p>
  </div>
</template>

<script setup>

defineProps(["title", "index", "paddingY"])
</script>

<style lang="scss" scoped>
@import url("~/assets/scss/projets/parcours/main.scss");

p {
  text-align: center;
  padding: 1rem;
  font-size: 1.5rem;
  border: 1px solid black;
  color: black;
}
</style>