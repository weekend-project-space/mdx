<script setup>
import micromark from "../utils/micromark";
import { debounce } from "lodash-es";
import { ref, computed, watch } from "vue";

const value = ref("");

const md = ref("");

function mdx(str) {
  if (str.indexOf("------") > 0) {
    let v = str.split("------");
    str = eval(v[0] + "`" + v[1] + "`");
  }
  return str;
}

watch(value, (v) => {
  debounce(() => {
    md.value = mdx(v);
  }, 3000)();
});
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
