<template>
  <div class="counter">
    <textarea name="text" id="text" @input="count"></textarea>
    <p>
      文字数: <span id="showCharCount">{{ charCount }}</span>
    </p>
    <p>
      行数: <span id="showLineCount">{{ lineCount }}</span>
    </p>
  </div>
</template>
<script lang="ts" setup>
import { ref } from "vue";
const charCount = ref(0);
const lineCount = ref(1);

const count = () => {
  const text = document.getElementById("text") as HTMLTextAreaElement;
  charCount.value = [...text.value].length;
  lineCount.value = text.value.split(/\r\n|\n|\r/).length;
};
</script>
<style lang="scss">
.counter {
  display: flex;
  justify-content: center;
  justify-items: stretch;
  margin: auto;
  width: 80vw;
  height: 80vh;
  flex-wrap: wrap;
  #text {
    display: block;
    width: 100%;
    height: 30em;
    max-height: 70%;
    padding: 1rem;
    resize: none;
    font-size: 1.3em;
    &:focus {
      outline: none;
    }
  }
  p {
    margin: 0.5rem;
  }
}
</style>
