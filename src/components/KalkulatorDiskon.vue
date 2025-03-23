<script setup>
import { ref, computed } from 'vue'

const harga = ref('')
const diskon = ref('')

const hargaSetelahDiskon = computed(() => {
    return harga.value - (harga.value * diskon.value) / 100
})

</script>

<template>
    <div class="container">
        <h2>Harga Setelah Diskon</h2>

        <label for="harga">Harga: </label>
        <input v-model="harga" type="number" name="harga" placeholder="Masukkan Harga...">
        <br> <br>
        
        <label for="diskon">Diskon: </label>
        <input v-model="diskon" type="number" name="diskon" placeholder="Masukkan Diskon"> %
        
        <p class="result">Harga : {{ hargaSetelahDiskon }}</p>
    </div>
</template>

<style scoped>
    .result {
        font-weight: bold;
    }
</style>