<script setup>
import { ref } from "vue";
import pageFrist from "./pageFrist.vue";
import pageContent from "./pageContent.vue";
import pageFooter from "./pageFooter.vue";
defineProps({
  msg: String,
});
const emit = defineEmits(["handleModal"]);

const count = ref(0);
</script>

<template>
  <pageFrist></pageFrist>
  <pageContent />
  <pageFooter @handleModal="emit('handleModal')" />
</template>

<style scoped></style>
