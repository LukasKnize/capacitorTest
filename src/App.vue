<script setup>
import { reactive, ref } from "vue";
import Pic from "./components/pictureFrame.vue";

let images = reactive({img: []});

async function loadImages() {
    let x = await fetch("https://api.waifu.pics/many/sfw/waifu", {
        method: "POST",
        headers: {
            "Content-Type": "application/json",
        },
        body: JSON.stringify({}),
    });

    x.json().then((xx) => {
        images.img = JSON.parse(JSON.stringify(xx.files));
    });
}

loadImages();
</script>

<template>
<header>
  <p>KawaiiDit</p>
  <button @click="loadImages()">reload</button>
</header>
    <Pic v-for="(img, index) in images.img" :key="index" :img="img" />
</template>

<style scoped>
header {
  height: 40px;
  width: 100%;
  background: #B91372;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99;
}

button {
  background: none;
  text-decoration: white underline;
}
</style>
