<script setup>
import {ref, defineEmits, defineProps} from 'vue'

defineProps(['inicio','fin','postSize'])
const emit = defineEmits(['next','prev'])

const activarPrev = () => {
    console.log('Pulsado Anterior')
    emit('prev')
}

const activarNext = () => {
    console.log('Pulsado Siguiente')
    emit('next')
}
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button @click="activarPrev" type="button" class="btn btn-outline-primary" :disabled="inicio === 0">Previous</button>
        <button @click="activarNext" type="button" class="btn btn-outline-primary" :disabled="fin >= postSize">Next</button>
    </div>
</template>
