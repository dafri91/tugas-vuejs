<script setup>
import { ref } from 'vue'

const name = ref('Budi')
const age = ref(25)

const time = ref(new Date().toLocaleTimeString('id-ID'))

setInterval(() => {
    time.value = new Date().toLocaleTimeString('id-ID')
}, 1000);
</script>

<template>
<h1>Belajar Text Interpolation</h1>

<p>Halo namaku {{ name }}, aku berumur {{ age }} tahun</p>
<p>Waktu sekarang : {{ time }}</p>
</template>

<style scoped>

</style>