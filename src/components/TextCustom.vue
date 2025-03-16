<script setup>
import { ref } from 'vue'

const textColor = ref('#000000')
const textSize = ref(20)


</script>

<template>
<h1 :style="{color:textColor, fontSize:textSize + 'px'}"> Text bisa berubah Warna</h1>

<label for="">Pilih warna text</label>
<input type="color" v-model="textColor">

<label for="">Ukuran Text</label>
<input type="range" v-model="textSize" min="5" max="50">
</template>

<style scoped>

</style>