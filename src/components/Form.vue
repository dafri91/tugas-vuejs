<script setup>
import { ref } from 'vue'

const name = ref('')
const usia = ref('')
const email = ref('')
const jenisKelamin = ref('')


const reset = () =>{
    name.value= ''
    usia.value= ''
    email.value= ''
    jenisKelamin.value= ''

}

</script>

<template>
    <h1>Formulir</h1>
<form>
    <label for="">Nama: </label>
    <input v-model= "name" type="text" name="name" placeholder="Masukkan Nama">
    <br> <br>
    <label for="">Usia: </label>
    <input v-model= "usia" type="number" name="usia" placeholder="Masukkan usia">
    <br> <br>
    <label for="email">Email :</label>
    <input v-model= "email" type="email" name="email" placeholder="Masukkan Email">
    
    <br> <br>
    <label for="jenisKelamin">Jenis Kelamin: </label>
    <label for=""><input v-model= "jenisKelamin" type="radio" value="Laki-Laki">Laki-Laki</label>
    <label for=""><input v-model= "jenisKelamin" type="radio" value="Perempuan">Perempuan</label>
    <br> <br>
    <button @click= "reset">Reset</button>
</form>

<div>
    <h1>Hasil Input </h1>
    <p>Nama: {{ name }}</p>
    <p v-if="usia">Usia: {{ usia }} tahun</p>
    <p v-else="usia">Usia: </p>
    <p>Email: {{ email }}</p>
    <p>Jenis Kelamin: {{ jenisKelamin }}</p>
</div>
</template>

<style scoped>

</style>