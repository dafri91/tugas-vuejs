<script setup>
import { ref, watch, computed } from 'vue'

const counter = ref(0)
const pesan = ref('')
const status = ref(false)

const increment = () => {
    counter.value ++
};

const decrement = () => {
    if(counter.value> 0 ) {
        counter.value--
    }
};

const kondisi = computed(() => {
    return counter.value !== 0 && counter.value % 5 == 0 
})

watch (counter, (newVal, oldVal) => {
    if(kondisi.value) {
        pesan.value = `Counter ke ${newVal}, kelipatan 5!`
        status.value = true
    }else {
        pesan.value = `Counter dari ${oldVal} ke ${newVal} `
        status.value = false
    }
})
</script>

<template>
    <div class="container">
        <h1>Watch Conter</h1>
        <p :style="{color: kondisi ? 'green' : 'black'}">Nilai : {{ counter }}</p>
        <button @click="decrement">Kurang</button>
        <button @click="increment">Tambah</button>

        <p :style="{color: kondisi ? 'blue' : 'black'}">{{ pesan }}</p>
    </div>
</template>

<style scoped>
    .container{
        text-align: center;
    }

    button{
        margin-right:5px;
    }

    p{
        font-size: 20px;
    }
</style>


