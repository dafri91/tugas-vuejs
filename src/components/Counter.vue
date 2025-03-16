<script setup>
import { ref } from 'vue'

const count = ref(0)

const pengurangan = () =>{
    if (count.value >0 ) {
        count.value--
    }
}


const reset = () =>{
    count.value = 0
}
</script>

<template>
<p>Nilai : {{ count }}</p>
<button @click = "count++">Tambah</button>
<button @click= "pengurangan">kurang</button>
<button @click= "reset">reset</button>
</template>

<style scoped>

</style>