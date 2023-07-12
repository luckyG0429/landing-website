<script setup>
import { ref } from "vue";
import picA from "../../assets/images/content-a.svg";
import picB from "../../assets/images/content-b.svg";
import picC from "../../assets/images/content-c.svg";
import picD from "../../assets/images/content-d.svg";
defineProps({
  msg: String,
});

const count = ref(0);
const picList = [picA, picB, picC, picD];
</script>

<template>
  <div class="page-content">
    <div class="content-title">
      Say what you wanna say, do what you wanna do
    </div>
    <div class="content-desc">
      From Secrets to Confessions: Share the Unspoken with Your Friends' AI Pal
      In this era, there is only what you can’t imagine, never what you can’t
      say
    </div>
  </div>
  <div class="content-list">
    <div
      class="content-item"
      v-for="(item, index) in picList"
      :key="index"
      :style="{ backgroundImage: `url(${item})` }"
    ></div>
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/scss/common.scss";
.page-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: px2rem(70);
}

.content-title {
  width: px2rem(842);
  font-size: px2rem(36);
  font-weight: 800;
  line-height: px2rem(50);
  height: px2rem(50);
  letter-spacing: 0em;
  text-align: left;
  word-break: keep-all;
  position: relative;

  &::after {
    position: absolute;
    content: "";
    bottom: px2rem(8);
    left: 0;
    width: 100%;
    height: px2rem(8);
    background-color: rgba(255, 12, 87, 1);
    z-index: -1;
  }
}

.content-desc {
  width: px2rem(832);
  padding: 0 px2rem(80);
  margin-top: px2rem(30);
  box-sizing: border-box;
  font-family: Poppins;
  font-size: px2rem(18);
  font-weight: 500;
  line-height: px2rem(32);
  letter-spacing: 0em;
  text-align: left;
  color: rgba(107, 98, 94, 1);
}

.content-list {
  display: inline-flex;
  flex-direction: row;
  margin-top: px2rem(60);
  flex-wrap: wrap;
  max-width: px2rem(1130);
}

.content-item {
  width: px2rem(565);
  height: px2rem(700);
  display: inline-block;
  background-size: 105% 105%;
  background-position: center center;
}

@media only screen and (max-width: 640px) {
  .page-content {
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-top: px2rem(24);
  }
  .content-title {
    width: xspx2rem(230);
    height: px2rem(100);
    text-align: center;
  }

  .content-desc {
    width: xspx2rem(327);
    padding: 0 px2rem(80);
    margin-top: px2rem(30);
  }
  .content-list {
    max-width: 100vw;
    min-width: xspx2rem(320);
    flex-direction: column;
  }

  .content-item {
    width: xspx2rem(327);
    height: xspx2rem(404);
    display: inline-block;
    background-size: 105% 105%;
    background-position: center center;
  }
}
</style>
