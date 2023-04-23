<script setup>
import micromark from "../utils/micromark";
import { ref, computed } from "vue";

const value = ref("");

const md = computed(() => mdx(value.value));

function mdx(str) {
  if (str.indexOf("------") > 0) {
    let v = str.split("------");
    str = eval(v[0] + "`" + v[1] + "`");
    console.log(str);
    return str;
  } else {
    return str;
  }
}
</script>
<template>
  <div class="grid">
    <textarea class="form-control" v-model="value" rows="9"></textarea>
    <div v-html="micromark(md)"></div>
  </div>
</template>

<style lang="less" scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 2rem;
}
</style>
