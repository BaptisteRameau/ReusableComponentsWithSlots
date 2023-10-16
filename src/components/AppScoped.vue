<template>
    <slot name="scoped" :message="message" :message2="message2"/>
</template>

<script setup>
import {ref, defineProps} from 'vue'

const message = ref('Hello Web team !')
//const message2 = ref('Hello tonton Gégé !')
defineProps({
    message2: { type: String, default: 'Hello tonton Gégé !'}
})
</script>