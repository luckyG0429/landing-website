<script setup>
import { ref } from "vue";
import axios from "axios";
import stepA from "./stepA.vue";
import stepB from "./stepB.vue";
import stepC from "./stepC.vue";

defineProps({
  msg: String,
});
const emit = defineEmits(["closeModal", "updateEmail"]);
const count = ref(1);
const file = ref(null);
const userEmail = ref(null);

function handleStep(param = true) {
  if (param) {
    if (count.value == 3) {
      return handleSubmit();
    }
    count.value++;
  } else {
    count.value--;
  }
}

function updateEmail(param) {
  console.log(param);
  userEmail.value = param;
}
function handleSubmit() {
  const landingPostTime = localStorage.getItem("landingPostTime");
  const now = Data.now();
  if (!landingPostTime || now - landingPostTime * 1 > 1000 * 26 * 60 * 60) {
    axios({
      method: "post",
      url: "/user/12345",
      data: {
        firstName: "Fred",
        lastName: "Flintstone",
      },
    }).then((res) => {
      /**  
      1. 提交代码成功后，设置缓存
      2. 提示成功 - 多少位 
      **/
      localStorage.setItem("landingPostTime", now);
      count.value++;
    });
  } else {
    // 提示：无法重复提交
  }
}

function close() {
  emit("closeModal", 1);
  count.value = 1;
}
</script>

<template>
  <div class="modal-layout">
    <div class="modal">
      <div class="modal-close" @click="close"></div>
      <div class="modal-title">
        {{
          count == 3
            ? "Congratulations, your AI self will be waiting for you in your inbox:"
            : "3 Steps, and you will have your one and only AI self"
        }}
      </div>
      <div class="modal-content">
        <stepA v-if="count == 1" />
        <stepB v-else-if="count == 2" />
        <stepC
          v-else-if="count == 3"
          :userEmail="userEmail"
          @updateEmail="(param) => updateEmail(param)"
        />
      </div>
      <div class="modal-btns">
        <div
          class="modal-last-btn"
          v-if="count == 2 || count == 3"
          @click="handleStep(false)"
        >
          Back
        </div>
        <div class="modal-next-btn" @click="handleStep">
          {{ count < 3 ? "Next" : "Submit" }}
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import "../../assets/scss/common.scss";

.modal-layout {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 233, 238, 0.98);
  padding: px2rem(80) px2rem(135);
  height: 100vh;
  overflow-y: scroll;
  box-sizing: border-box;
  transform: scale(0.2);
  opacity: 0.5;
  transition: all 0.3s linear;
}

.show-modal {
  animation: showModal 0.5s ease-out 1;
  animation-delay: 0.1s;
  animation-fill-mode: forwards;
}

@keyframes showModal {
  50% {
    opacity: 1;
  }

  78% {
    transform: scale(1.1);
    opacity: 1;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}
.modal {
  width: 100%;
  text-align: left;
  postion: relative;
  .modal-close {
    position: absolute;
    width: px2rem(42);
    height: px2rem(42);
    background-image: url("../../assets/images/icon-close.svg");
    background-size: 100%;
    top: px2rem(80);
    right: px2rem(85);
    cursor: pointer;
  }
  .modal-title {
    font-size: px2rem(32);
    font-weight: 800;
    line-height: px2rem(66);
    height: px2rem(66);
    letter-spacing: 0em;
    text-align: left;
    color: $text-1;
    margin-bottom: px2rem(48);
  }

  .modal-content {
    &-title {
      font-size: px2rem(24);
      font-weight: 900;
      line-height: px2rem(33);
      height: px2rem(33);
      letter-spacing: 0em;
      color: $text-1;
      text-align: left;
      margin-bottom: px2rem(32);
    }

    &-desc {
      font-family: Nunito;
      font-size: px2rem(20);
      font-weight: 600;
      line-height: px2rem(28);
      letter-spacing: 0em;
      text-align: left;
      color: $text-1;
      opacity: 0.5;
      margin-bottom: px2rem(32);
    }
  }
}

.modal-btns {
  display: flex;
  height: px2rem(120);
  align-items: center;
}
.modal-next-btn {
  width: px2rem(240);
  height: px2rem(60);
  border-radius: px2rem(30);
  border: px2rem(2) solid $line-bg1;
  color: #fff;
  background: $line-bg1;
  font-size: px2rem(24);
  font-weight: 900;
  line-height: px2rem(60);
  letter-spacing: 0em;
  box-sizing: border-box;
  text-align: center;
}
.modal-last-btn {
  width: px2rem(240);
  height: px2rem(60);
  box-sizing: border-box;
  border-radius: px2rem(30);
  border: px2rem(4) solid $line-bg1;
  color: $line-bg1;
  background-color: #fff;
  font-size: px2rem(24);
  font-weight: 900;
  line-height: px2rem(60);
  letter-spacing: 0em;
  text-align: center;
  margin-right: px2rem(20);
}

@media only screen and (max-width: 640px) {
  .modal {
    .modal-title {
      min-height: xspx2rem(44);
      height: auto;
      margin-bottom: xspx2rem(5);
    }
    .modal-close {
      top: xspx2rem(10);
      right: xspx2rem(10);
    }
    .modal-content {
      padding-top: xspx2rem(10);

      &-title {
        margin-bottom: xspx2rem(5);
        min-height: xspx2rem(22);
        height: auto;
        line-height: xspx2rem(22);
      }
    }
  }
}
</style>
