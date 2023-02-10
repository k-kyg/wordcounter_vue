<template>
  <div class="counter">
    <textarea name="text" id="text" @input="count"></textarea>
    <p>
      文字数: <span id="show_the_number_of_chars">{{ char_count }}</span>
    </p>
    <p>行数: <span id="show_the_number_of_rows">0</span></p>
  </div>
</template>
<script lang="ts" setup>
import { ref } from "vue";
let char_count = ref(0);

const count = () => {
  const text = document.getElementById("text") as HTMLTextAreaElement;
  char_count.value = [...text.value].length;
  document.getElementById("show_the_number_of_chars")?.textContent !=
    char_count.value.toString();
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
