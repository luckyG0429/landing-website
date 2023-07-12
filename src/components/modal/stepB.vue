<script setup>
import { ref } from "vue";
import processLine from "./process.vue";

defineProps({
  msg: String,
});

const count = ref(0);

const uploadTips = ref("");
const uploadFile = ref("");

function handleLink() {
  location.href = "";
}
function handleFile(e) {
  var files = e.target.files;
  //   setPicInput(files[0].name);
  if (files.length) {
    var tmppath = URL.createObjectURL(e.target.files[0]);
    console.log({ name: files[0].name, type: files[0].type, path: tmppath });
    let fileType = files[0].type;
    let fileSize = files[0].size;
    uploadFile.value = files[0].name;
    //1. 文件格式正确； 2 文件大小不易过大
    if (fileType != "application/zip") {
      return (uploadTips.value = "please zip the file");
    } else if (fileSize > 1024 * 1024 * 1024) {
      return (uploadTips.value = "file size too large");
    }
    uploadTips.value = "";
    var reader = new FileReader();
    reader.onload = function (e) {
      console.log(reader.result);
      // setPic(reader.result as string);
    };

    setModal(2, {
      name: files[0].name,
      type: files[0].type,
      path: tmppath,
    });
    reader.readAsDataURL(files[0]);
  }
}
</script>

<template>
  <div class="modal-content-line">
    <div class="modal-content-title">Step 2: Upload Zip</div>
    <processLine />
    <div class="modal-content-desc">
      After 15 minutes to a maximum of 24 hours, your request will be accepted
      by Facebook, and the download option will be visible in the Available
      Files option. We recommend uploading the entire zip directly.
    </div>
  </div>
  <div class="modal-content-line">
    <div class="modal-content-file">
      <input type="file" @change="(e) => handleFile(e)" />
      <span class="modal-content-file-text" v-if="!uploadFile"
        >Upload file</span
      >
      <span
        class="modal-content-file-text2"
        :class="uploadTips ? 'warn' : 'suc'"
        v-else
        >{{ uploadFile }}</span
      >
    </div>
  </div>
  <div class="modal-content-spanline">
    <span class="modal-content-span">
      However, if you have concerns or wish to select several chats, you can:
    </span>
    <ol>
      <li class="modal-content-span">
        Right-click on the file to extract the file.
      </li>
      <li class="modal-content-span">
        Open the Inbox folder and your all chats in json formats
      </li>
      <li class="modal-content-span">
        Select several people’s chat histories to upload
      </li>
    </ol>
  </div>

  <div class="modal-poctoal" @click="handleLink">Data Privacy Disclaimers</div>
</template>

<style lang="scss" scoped>
@import "../../assets/scss/common.scss";
.modal-content-file {
  width: px2rem(500);
  height: px2rem(220);
  border: px2rem(2) dashed $line-bg1;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: px2rem(24);

  input[type="file"] {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    opacity: 0;
    z-index: 9;
  }

  &-text {
    font-family: Nunito;
    font-size: px2rem(24);
    font-weight: 900;
    line-height: px2rem(33);
    letter-spacing: 0em;
    text-align: center;
    width: px2rem(240);
    padding: px2rem(23) 0;
    border-radius: px2rem(4);
    border: px2rem(2) solid #fff;
    background-color: #fff;
    color: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0.85;

    &::before {
      content: "";
      width: px2rem(32);
      height: px2rem(32);
      background-image: url("../../assets/images/icon-upload.svg");
      background-size: 100%;
      display: inline-block;
      margin: 0 px2rem(12);
    }
  }
  &-text2 {
    font-family: Nunito;
    font-size: px2rem(24);
    font-weight: 900;
    line-height: px2rem(33);
    letter-spacing: 0em;
    text-align: center;
    min-width: px2rem(240);
    padding: px2rem(23) px2rem(12);
    border-radius: px2rem(4);
    border: px2rem(2) solid #fff;
    background-color: #fff;
    color: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0.85;

    &.suc::before {
      content: "";
      width: px2rem(32);
      height: px2rem(32);
      background-image: url("../../assets/images/icon-suc.svg");
      background-size: 100%;
      display: inline-block;
      margin-right: px2rem(12);
    }

    &.warn::before {
      content: "";
      width: px2rem(32);
      height: px2rem(32);
      background-image: url("../../assets/images/icon-warn.svg");
      background-size: 100%;
      display: inline-block;
      margin-right: px2rem(12);
    }
  }
}
.modal-content-spanline {
  display: flex;
  flex-direction: column;

  ol {
    margin: 0;
    padding-left: px2rem(26);
  }
}
.modal-content-span {
  font-family: Nunito;
  font-size: px2rem(20);
  font-weight: 600;
  line-height: px2rem(28);
  letter-spacing: 0em;
  text-align: left;
  color: $text-1;
  opacity: 0.5;
}

.modal-poctoal {
  margin-top: px2rem(24);
  font-family: Nunito;
  font-size: px2rem(16);
  font-weight: 400;
  line-height: px2rem(24);
  letter-spacing: 0em;
  text-align: left;
  color: $line-bg1;
  cursor: pointer;

  &:hover {
    text-decoration: underline;
  }
}
</style>
