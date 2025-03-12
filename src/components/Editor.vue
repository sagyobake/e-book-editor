<script setup>
import { ref } from 'vue';

const message = ref('');

defineProps({
    msg: String,
});

const download = (event) => {
    const blob = new Blob([message.value], { type: 'text/plain' });
    const url = URL.createObjectURL(blob);

    event.target.href = url; // Set the href dynamically
    event.target.download = "Manuscript.txt"; // Set the download filename
};
</script>

<template>
    <textarea v-model="message" placeholder="Start writing here."></textarea>
    <a href="#" @click="download">{{ msg }}</a>
</template>
