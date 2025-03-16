<script setup>
import { ref } from 'vue'

const isLoggedIn = ref(false)
const username = ref('')
const password = ref('')

const toggleLogin = ()=>{
    isLoggedIn.value = !isLoggedIn.value
    if (!isLoggedIn.value) {
        username.value = ""
        pass.value = ""
    }
}

</script>

<template>
<div class="container">
    <h1>{{ isLoggedIn ? `Selamat Datang ${username}` : `Silahkan Login`  }}</h1>

    <div v-if="!isLoggedIn">
    <input v-model="username" type="text" placeholder="Nama" />
    <br> <br>
    <input v-model="password" type="password" placeholder="Password" />
    </div>
     <br>
    <button @click="toggleLogin" :disabled="isLoggedIn && (!username || !password)">{{ isLoggedIn ? "Logout":"Login" }}</button>
    <p>{{ isLoggedIn ? "Login Berhasil" : "Belum Login" }}</p>
</div>
</template>

<style scoped>

</style>