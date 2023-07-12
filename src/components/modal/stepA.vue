<script setup>
import { ref } from "vue";
import processLine from "./process.vue";

defineProps({
  msg: String,
});

const count = ref(0);
const stepObj = ref({
  title: " Step 1: Request History from Facebook Messenger",
  desc: "Follow these steps to obtain all your chat history from your Facebook Messenger:",
});
</script>

<template>
  <div class="modal-content-line">
    <div class="modal-content-title">{{ stepObj.title }}</div>
    <div class="modal-content-desc">{{ stepObj.desc }}</div>
    <processLine />
  </div>
  <div class="modal-content-line">
    <div class="modal-content-title">Then choose</div>
    <div>
      <div>
        <span></span>
        <span></span>
      </div>
    </div>
    <div class="modal-content-desc">
      Recommended Data Size: 2,000 messages, so we recommend 6-month for your
      date range
    </div>
  </div>
  <div class="modal-content-line">
    <div class="modal-content-title">Finally: click</div>
    <div class="modal-content-btnText">Request to download</div>
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/scss/common.scss";
.modal-content-line {
  width: 100%;
}

.modal-content-btnText {
  width: px2rem(360);
  height: px2rem(44);
  border-radius: px2rem(22);
  border: px2rem(2) solid $line-bg1;
  font-size: px2rem(12);
  line-height: px2rem(44);
  letter-spacing: 0em;
  font-family: "Nunito";
  text-align: center;
  color: $line-bg1;
  background-color: #fff;
}
@media only screen and (max-width: 640px) {
  .modal-content-title {
    margin-bottom: xspx2rem(20);
  }
}
</style>
