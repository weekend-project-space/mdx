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
    localStorage.setItem("mdx-value", v);
    md.value = mdx(v);
  }, 1000)();
});
value.value = localStorage.getItem("mdx-value");
</script>
<template>
  <div class="grid">
    <textarea class="form-control" v-model="value" rows="9"></textarea>
    <div v-html="micromark(md)" class="form-control page"></div>
  </div>
</template>

<style lang="less" scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 2rem;
}
.page {
  background: #f9f9f9;
}
</style>
