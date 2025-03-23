<script setup>
import { ref, onBeforeMount, onMounted, onUpdated } from 'vue'

const hours = ref(0)
const minutes = ref(0)
const seconds = ref(0)
const timer = ref(null)

const startTimer = () => {
    if(!timer.value) {
        timer.value = setInterval(()=>{
            seconds.value++

            if(seconds.value == 60) {
                seconds.value = 0
                minutes.value++
            }

            if (minutes.value == 60 ) {
                minutes.value = 0 
                hours.value++
            }
        }, 1000)
    }
};

const pauseTimer = () => {
    clearInterval(timer.value)
    timer.value = null
};

const resetTimer = () => {
    pauseTimer()
    hours.value  = 0
    minutes.value  = 0
    seconds.value  = 0
};

const formatTimer = (n) => {
    return n < 10 ? `0${n}`: `${n}`
};


onBeforeMount(() => {
    console.log(`Komponen akan dimuat`);
    
})

onMounted(() => {
    console.log(`Komponen telah dimuat`);
    
})


onUpdated(() => {
    console.log(`waktu yang diperbarui : ${ formatTimer(hours.value) } : ${ formatTimer(minutes.value) } : ${ formatTimer(seconds.value) }`);   
})
</script>

<template>
    <div class="container">
        <h1> ⏲Timer</h1>
        <p class="display-timer">{{ formatTimer(hours) }} : {{ formatTimer(minutes) }} : {{ formatTimer(seconds) }}</p>

        <button @click="startTimer">Start</button>
        <button @click="pauseTimer">Pause</button>
        <button @click="resetTimer">Reset</button>
    </div>
</template>

<style scoped>
    .container{
        text-align: center;
    }

    button{
        margin: 5px;
        padding-inline: 10px;
        padding-block: 5px;
        background-color: aquamarine;
        
    }

    button:hover {
    background-color: #76eec6;
    }
    
    p{
        font-size: 20px;
    }
</style>
