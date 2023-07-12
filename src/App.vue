<script setup>
import { ref } from "vue";
import index from "./components/index/index.vue";
import modal from "./components/modal/index.vue";

const showModal = ref(false);
function handleModal(param = true) {
  showModal.value = !!param;
}
</script>

<template>
  <index msg="Vite + Vue" @handleModal="handleModal" />
  <modal
    v-show="showModal"
    :class="showModal ? 'show-modal' : ''"
    @closeModal="handleModal(false)"
  />
</template>

<style scoped>
html,
body {
  padding: 0 0;
  margin: 0 0;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
