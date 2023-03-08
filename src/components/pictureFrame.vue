<template>
    <div class="container">
        <img :src="props.img" alt="">
        <div class="controllBar">
            <button @click="love()">
                <img :src="loveIcon.path" alt="">
            </button>
            <button @click="copy()">
                <img src="../assets/copy.svg" alt="">
            </button>
        </div>
    </div>
</template>

<style scoped>
.container{
    width: 100%;
    max-height: 80vh;
    height: auto;
    margin-top: 10px;
}

.container img{
    max-height: calc(80vh - 40px);
    width: 100%;
}

.container .controllBar {
    width: 100%;
    height: 40px;
    background-color: #2C2B29;
    border: #131210 1px solid;
    display: flex;
}

.container .controllBar button{
    background: none;
    border: none;
    height: 40px;
    width: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.container .controllBar button img{
     height: 40px;
    width: 40px;
}
</style>

<script setup>
import { reactive } from "vue"

let props = defineProps({
  img: String,
})

let loveIcon = reactive({path: "./src/assets/fav0.svg"})

function love(){
    if (loveIcon.path == "./src/assets/fav0.svg") {
        loveIcon.path = "./src/assets/fav1.svg"
    }else{
        loveIcon.path = "./src/assets/fav0.svg"
    }
}

function copy(){
    navigator.clipboard.writeText(props.img)
}
</script>