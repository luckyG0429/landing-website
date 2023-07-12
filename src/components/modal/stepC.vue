<script setup>
import { ref, onMounted } from "vue";

const props = defineProps({
  msg: String,
  userEmail: String,
});

const emit = defineEmits(["updateEmail"]);

const count = ref(0);
const inputEmail = ref("");
const errorText = ref("");
onMounted(() => {
  inputEmail.value = props.userEmail;
});

function checkEmail(e) {
  console.log(e.target.value);
  const email = e.target.value;
  const emailCheck = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g;
  const result = emailCheck.test(email.trim());
  if (!result) {
    inputEmail.value = email;
    errorText.value = "Require a valid email";
    return false;
  } else {
    errorText.value = "";
    inputEmail.value = email;
    emit("updateEmail", email);
  }
}
</script>

<template>
  <div class="modal-content-line">
    <div class="modal-content-title">Email address:</div>
    <div class="modal-content-input">
      <input
        class="modal-content-input-inner"
        type="text"
        :value="inputEmail"
        @change="(e) => checkEmail(e)"
      />
      <span class="modal-content-input-error">{{ errorText }}</span>
    </div>
  </div>
</template>

<style lang="scss" scope>
@import "../../assets/scss/common.scss";
.modal-content-input {
  width: px2rem(600);
  height: px2rem(64);
  border-radius: px2rem(6);
  position: relative;
  margin-bottom: px2rem(32);
  border: px2rem(2) solid rgba(0, 0, 0, 0.4);
  &-inner {
    position: absolute;
    border: 0;
    top: px2rem(8);
    left: px2rem(12);
    right: px2rem(12);
    height: px2rem(48);
    outline: transparent;
    background: transparent;
    -webkit-tap-highlight-color: transparent;
  }
  &-error {
    position: absolute;
    border: 0;
    bottom: px2rem(-38);
    left: px2rem(12);
    right: px2rem(12);
    height: px2rem(32);
    line-height: px2rem(32);
    font-size: px2rem(22);
    color: $line-bg1;
  }
}
@media only screen and (max-width: 640px) {
  .modal-content-input {
    width: xspx2rem(256);
    height: xspx2rem(32);
    border-radius: px2rem(6);
    position: relative;
    margin-bottom: xspx2rem(25);
    border: px2rem(2) solid rgba(0, 0, 0, 0.4);
    &-error {
      position: absolute;
      border: 0;
      bottom: xspx2rem(-25);
      left: xspx2rem(2);
      right: xspx2rem(2);
      height: xspx2rem(22);
      line-height: xspx2rem(22);
      font-size: xspx2rem(12);
      color: $line-bg1;
    }
  }
}
</style>
