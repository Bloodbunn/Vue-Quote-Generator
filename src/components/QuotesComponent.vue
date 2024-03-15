<template>

    <div class="w-[500px] max-[520px]:w-[90%]  p-4 mx-auto mt-10 border border-gray-200 shadow-md">
        <h1 class="text-2xl max-[520px]:text-xl  font-bold ">Random Quote Generator</h1>
        <div class="flex justify-center items-center flex-col mt-4 bg-gray-100 p-5 max-[520px]:p-3 h-[300px] max-[520px]:h-[200px]">
            <p class="text-xl text-black">"{{ currentQuote.text }}"</p>
            <span class="text-sm italic inline-block text-gray-500 mt-3">{{ currentQuote.author }}</span>
        </div>

        <button @click="getRandomQuote" class="bg-blue-500 text-white hover:bg-blue-700 transition-all duration-300 px-2 py-1 rounded mt-3">Get Random Quote</button>
    </div>

</template>

<script setup>
import { ref, onMounted } from 'vue'
const currentQuote = ref({text: '', author: ''}) //can also make this an empty ref('') or an emtpy ref object ref({}). it will still work. 

const quotes = ref([
    {
        text: "My precious!",
        author: "Gollum",
    },
    {
        text: "All we have to decide is what to do with the time that is given us.",
        author: "Gandalf",
    },
    {
        text: "Not all those who wander are lost.",
        author: "Bilbo Baggins",
    },

    {
        text:"Ride to ruin and the world's ending!",
        author:"Theoden"
    },
    {
        text:"It is not despair, for despair is only for those who see the end beyond all doubt. We do not.",
        author:"Gandalf"
    },
    {
        text:"If By My Life Or Death I Can Protect You, I Will.",
        author:"Aragorn"
    }


])

const getRandomQuote = () => {
    const randomIndex = Math.floor(Math.random() * quotes.value.length)
    currentQuote.value = quotes.value[randomIndex] //now currentQuote and the ojbect of the quotes that lies at that index of the array both contain the same object. Not making a new memory of it, but a reference to the same object.
}

onMounted(getRandomQuote)





</script>