<template>
    <slot name="test" :test2="message" :test3="message2">
    <p>{{ message }}</p>
    <p>{{ message2 }}</p>
    </slot>
</template>

<script setup>
import {ref, defineProps} from 'vue'

const message = ref('Hello Web team !')
//const message2 = ref('Hello tonton Gégé !')
defineProps({
    message2: { type: String, default: 'Hello tonton Gégé !'}
})
</script>