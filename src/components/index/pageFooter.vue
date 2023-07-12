<script setup>
import { ref } from "vue";

const emit = defineEmits(["handleModal"]);
defineProps({
  msg: String,
});

const count = ref(0);

function showModal() {
  emit("handleModal");
}
function handleLink(param) {
  let targetURL = "";
  if (param == "facebook") {
    targetURL = "";
  } else {
    targetURL = "https://twitter.com/URS__ai";
  }
  location.href = targetURL;
}
</script>

<template>
  <div class="page-footer">
    <div class="footer-content">
      <div class="footer-content-title">
        Unlock New Social Experience in the AI Era
      </div>
      <div class="footer-content-btn" @click="showModal">Create UR AI NOW</div>
      <div class="footer-content-desc">Fill Out Questionnaire Instead</div>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-bottom-logo"></div>
    <div class="footer-bottom-co">
      <span class="footer-bottom-co-text">
        Copyright @ Milton Debnath 2020, All rights reserved
      </span>
      <span class="footer-bottom-co-img">
        <span
          class="footer-bottom-co-icon to-facebook"
          @click="handldLink('facebook')"
        />
        <span
          class="footer-bottom-co-icon to-twitter"
          @click="handldLink('twitter')"
        />
      </span>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import "../../assets/scss/common.scss";
.page-footer {
  display: flex;
  padding-top: px2rem(120);
}
.footer-content {
  display: flex;
  margin: 0 auto;
  width: px2rem(1070);
  height: px2rem(320);
  flex-direction: column;
  align-items: center;
  margin-bottom: px2rem(40);
  position: relative;
  &::after {
    content: "";
    background-image: url("../../assets/images/footer-bg.svg");
    background-size: px2rem(320) px2rem(320);
    position: absolute;
    background-repeat: no-repeat;
    top: 0;
    left: 0;
    width: px2rem(320);
    height: px2rem(320);
    transform: rotateY(153deg);
  }
  &::before {
    content: "";
    background-image: url("../../assets/images/footer-bg.svg");
    background-size: px2rem(320) px2rem(320);
    position: absolute;
    background-repeat: no-repeat;
    top: 0;
    right: 0;
    width: px2rem(320);
    height: px2rem(320);
  }
}
.footer-content-title {
  font-size: px2rem(36);
  font-weight: 800;
  width: px2rem(427);
  line-height: px2rem(49);
  letter-spacing: 0em;
  text-align: center;
  position: relative;
  margin-bottom: px2rem(64);
  &::after {
    position: absolute;
    content: "";
    bottom: px2rem(8);
    left: 0;
    width: 100%;
    height: px2rem(8);
    background: $line-bg2;
    z-index: -1;
  }
}

.footer-content-btn {
  width: px2rem(360);
  height: px2rem(60);
  line-height: px2rem(60);
  border-radius: px2rem(30);
  background: $line-bg1;
  font-size: px2rem(20);
  font-weight: 800;
  letter-spacing: 0em;
  text-align: center;
  color: #fff;
  margin-bottom: px2rem(20);
  cursor: pointer;
}

.footer-content-desc {
  font-family: Inter;
  font-size: px2rem(20);
  font-weight: 600;
  line-height: px2rem(24);
  height: px2rem(24);
  letter-spacing: 0.1em;
  text-align: left;
  color: rgba(166, 166, 166, 1);
}

.footer-bottom {
  background: rgba(36, 16, 8, 1);
  width: 100vw;
  height: px2rem(250);
  overflow: hidden;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;

  &-logo {
    width: px2rem(155);
    height: px2rem(160);
    display: inline-block;
    margin: 0 auto;
    background-image: url("../../assets/images/footer-logo.svg");
    background-size: px2rem(155);
    background-repeat: no-repeat;
    background-position: center center;
  }

  &-co {
    height: px2rem(80);
    width: px2rem(1170);
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    border-top: 1px solid #aaa;
    align-items: center;
    margin: 0 auto;
    &-text {
      display: inline-block;
      align-self: center;
      font-family: Poppins;
      font-size: px2rem(16);
      font-weight: 400;
      line-height: px2rem(80);
      height: px2rem(80);
      letter-spacing: 0em;
      text-align: left;
      color: rgba(215, 215, 215, 1);
    }
    &-img {
      display: inline-flex;
      height: px2rem(30);
      width: px2rem(80);
      align-self: center;
    }

    &-icon {
      display: inline-block;
      width: px2rem(30);
      height: px2rem(30);
      background-position: center center;
      background-size: px2rem(30) px2rem(30);
      padding: 0 0;
    }
    .to-facebook {
      background-image: url("../../assets/images/icon-facebook.svg");
    }
    .to-twitter {
      margin-left: px2rem(12);
      background-image: url("../../assets/images/icon-twitter.svg");
    }
  }
}

@media only screen and (max-width: 640px) {
  .page-footer {
    display: flex;
    padding-top: xspx2rem(40);
  }
  .footer-content {
    width: xspx2rem(355);
    height: xspx2rem(137);
    font-size: xspx2rem(13);
    font-weight: 800;
    line-height: xspx2rem(18);
    &::after {
      content: "";
      background-image: url("../../assets/images/footer-bg.svg");
      background-size: xspx2rem(80);
      position: absolute;
      background-position: center center;
      background-repeat: no-repeat;
      top: 0;
      left: 0;
      width: xspx2rem(80);
      height: xspx2rem(137);
      transform: rotateY(153deg);
    }
    &::before {
      content: "";
      background-image: url("../../assets/images/footer-bg.svg");
      background-size: xspx2rem(80);
      position: absolute;
      background-position: center center;
      background-repeat: no-repeat;
      top: 0;
      right: 0;
      width: xspx2rem(80);
      height: xspx2rem(137);
    }
  }

  .footer-content-title {
    font-family: Nunito;
    font-size: xspx2rem(13);
    font-weight: 800;
    width: xspx2rem(155);
    line-height: xspx2rem(20);
    letter-spacing: 0em;
    text-align: center;
    position: relative;
    margin-bottom: xspx2rem(34);
    &::after {
      position: absolute;
      content: "";
      bottom: xspx2rem(4);
      left: 0;
      width: 100%;
      height: xspx2rem(4);
      background: $line-bg1;
      z-index: -1;
    }
  }
  .footer-content-desc {
    font-family: Inter;
    font-size: xspx2rem(10);
    font-weight: 600;
    line-height: xspx2rem(13);
    height: xspx2rem(13);
    letter-spacing: 0.1em;
    text-align: left;
    color: rgba(166, 166, 166, 1);
  }

  .footer-bottom {
    background: rgba(36, 16, 8, 1);
    width: 100vw;
    height: xspx2rem(220);
    overflow: hidden;
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    &-logo {
      width: xspx2rem(105);
      height: xspx2rem(110);
      display: inline-block;
      margin: 0 auto;
      background-image: url("../../assets/images/footer-logo.svg");
      background-size: xspx2rem(105);
      background-repeat: no-repeat;
      background-position: center center;
    }
    &-co {
      width: 100%;
      flex-direction: column-reverse;
      align-items: center;
      justify-content: center;
      mix-width: xspx2rem(320);
      height: xspx2rem(120);
      &-img {
        width: xspx2rem(64);
        height: xspx2rem(22);
      }

      &-icon {
        width: xspx2rem(22);
        height: xspx2rem(22);
        background-size: xspx2rem(22) xspx2rem(22);
      }

      .to-twitter {
        margin-left: xspx2rem(14);
      }
    }
  }
}
</style>
