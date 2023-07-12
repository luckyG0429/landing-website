<script setup>
import { ref } from "vue";
</script>

<template>
  <div class="page-header">
    <div class="page-header-inner">
      <div class="page-header-logo"></div>
      <div class="page-header-content">
        <div class="page-header-title">
          Party with<span class="marked"> UR AI </span>
          Pals on Palooza
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/scss/common.scss";
.page-header {
  width: 100vw;
  height: 100vh;
  background-color: $basic-color;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.page-header-inner {
  max-width: px2rem(1440);
  width: px2rem(1440);
  height: px2rem(970);
  max-height: px2rem(970);
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: px2rem(100);
  box-sizing: border-box;
}

.page-header-logo {
  position: absolute;
  width: px2rem(170);
  height: px2rem(50);
  top: px2rem(50);
  left: px2rem(160);
  background-image: url("../../assets/images/headerlogo.svg");
  background-size: px2rem(170);
}
.page-header-content {
  width: px2rem(1138);
  height: px2rem(703);
  background-image: url("../../assets/images/headerbg.svg");
  background-size: 100% 100%;
  position: relative;
}
.page-header-title {
  position: absolute;
  width: px2rem(800);
  min-height: px2rem(132);
  line-height: px2rem(66);
  top: px2rem(24);
  left: 50%;
  font-size: px2rem(54);
  transform: translateX(-50%);
  font-weight: 800;
  letter-spacing: 0;
  text-align: center;

  .marked {
    display: inline-block;
    background-color: $line-bg1;
    padding: 0 px2rem(10);
    margin-left: px2rem(4);
  }
}

@media only screen and (max-width: 640px) {
  .page-header {
    width: 100vw;
    max-width: 100vw;
    min-width: xspx2rem(320);
    height: xspx2rem(400);
    background-color: $basic-color;
  }

  .page-header .page-header-logo {
    position: absolute;
    width: xspx2rem(105);
    height: xspx2rem(27);
    top: xspx2rem(22);
    left: xspx2rem(24);
    background-image: url("../../assets/images/headerlogo.svg");
    background-size: xspx2rem(105);
  }
  .page-header .page-header-inner {
    width: 100vw;
    min-width: xspx2rem(320);
    height: xspx2rem(400);
    max-height: xspx2rem(400);
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    padding-top: xspx2rem(120);
    box-sizing: border-box;
  }

  .page-header .page-header-inner .page-header-content {
    width: 100vw;
    min-width: xspx2rem(320);
    height: xspx2rem(300);
    background-image: url("../../assets/images/headerbg-xs.svg");
    background-size: 100% 100%;
    position: relative;
  }

  .page-header-title {
    position: absolute;
    width: xspx2rem(240);
    min-height: px2rem(132);
    line-height: px2rem(66);
  }
}
</style>
