<script setup>
import { ref } from 'vue'

const pesan = ref('Silahkan Klik Tombol di bawah!')
const warna = ref('black')
const counter = ref(0)

const increment = () =>{
    counter.value ++
    pesan.value = `Halo, Kamu Telah klik ${counter.value} kali`

    warna.value = counter.value % 5 == 0 ? 'red' : 'black'
}

const reset = () => {
    counter.value = 0

    pesan.value = 'Silahkan Klik Tombol di bawah!'
    warna.value = 'black'
};

</script>

<template>
<h1 :style = "{color : warna}">{{ pesan }}</h1>

<button @click = "increment">klik</button>
<button @click = "reset">reset</button>
<p>total klik : {{ counter }}</p>
</template>

<style scoped>

</style>