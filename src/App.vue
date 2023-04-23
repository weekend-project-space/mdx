<script setup>
import Mdx from "./components/Mdx.vue";
</script>

<template>
  <div class="flex">
    <h1>mdx = md + x</h1>
    <a href="https://github.com/weekend-project-space/mdx" target="_blank"
      >源码</a
    >
  </div>

  <Mdx />
</template>
<style lang="less" scoped>
.flex {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
  a {
    margin-left: 1rem;
  }
}
</style>
