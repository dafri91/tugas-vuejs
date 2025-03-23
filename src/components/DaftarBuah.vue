<script setup>
import { ref } from 'vue'

const items = ref(['Apel', 'Mangga', 'Anggur'])

const newitem = ref('')

const addItem = () => {
    if(newitem.value.trim()){
        items.value.push(newitem.value.trim())
        newitem.value= ' '
    }
};
</script>

<template>
    <div class="container">
        <ul>
            <li v-for="(item, index) in items" :key="index">{{ item }}</li>
        </ul>

        <input v-model="newitem" type="text" name="daftar" placeholder="Masukkan Nama Buah....">
        <button @click="addItem">Tambah</button>
    </div>
</template>

<style scoped>
    input{
        margin-right: 10px;
    }
</style>
