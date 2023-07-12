<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});

const list = ref([
  "Profile",
  "Settings & Privacy",
  "Privacy",
  "Facebook information",
  "Download profile information",
]);
</script>

<template>
  <div class="modal-content-process">
    <span
      class="process-item"
      :class="list.length == index + 1 ? '' : 'otherpoint'"
      v-for="(item, index) in list"
      :key="index"
      >{{ item }}</span
    >
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/scss/common.scss";
.modal-content-process {
  display: flex;
  margin-top: px2rem(24);
  margin-bottom: px2rem(48);
  span.process-item {
    position: relative;
    font-family: Nunito;
    font-size: px2rem(15);
    font-weight: 700;
    line-height: px2rem(48);
    height: px2rem(48);
    letter-spacing: 0em;
    box-sizing: border-box;
    padding: 0 px2rem(20);
    border: px2rem(1) solid $line-bg1;
    border-radius: px2rem(30);
    background: rgba(255, 255, 255, 0.7);
    color: $line-bg1;
    display: inline-block;
    margin-right: px2rem(40);

    &.otherpoint::after {
      content: "";
      position: absolute;
      width: px2rem(30);
      top: 50%;
      right: px2rem(-35);
      height: px2rem(15);
      transform: translate(0, -50%);
      display: inline-block;
      background-image: radial-gradient(
        circle at center,
        $line-bg1 0%,
        $line-bg1 15%,
        transparent 50%,
        transparent 100%
      );
      background-size: px2rem(15) px2rem(15);
    }
  }
}
@media only screen and (max-width: 640px) {
  .modal-content-process {
    display: flex;
    margin-top: xspx2rem(24);
    margin-bottom: xspx2rem(12);
    flex-direction: column;
    span.process-item {
      position: relative;
      font-family: Nunito;
      font-size: px2rem(15);
      font-weight: 700;
      line-height: px2rem(48);
      height: px2rem(48);
      letter-spacing: 0em;
      box-sizing: border-box;
      padding: 0 px2rem(20);
      border: px2rem(1) solid $line-bg1;
      border-radius: px2rem(30);
      background: rgba(255, 255, 255, 0.7);
      color: $line-bg1;
      display: inline-block;
      text-align: center;
      margin-bottom: px2rem(45);

      &.otherpoint::after {
        content: "";
        position: absolute;
        width: px2rem(30);
        left: 50%;
        bottom: px2rem(-35);
        height: px2rem(15);
        transform: translate(-50%, px2rem(35));
        display: inline-block;
        background-image: radial-gradient(
          circle at center,
          $line-bg1 0%,
          $line-bg1 15%,
          transparent 50%,
          transparent 100%
        );
        background-size: px2rem(15) px2rem(15);
      }
    }
  }
}
</style>
