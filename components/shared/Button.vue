<template>
    <button v-if="color == 'purple'" class="bg-purple rounded-lg   py-3 px-6 text-white font-bold">
        {{ message }}
    </button>
    <button v-else class="bg-white rounded-lg   py-3 px-6 text-black font-bold">
        {{ message }}
    </button>
</template>
<script setup lang="ts">
defineProps<{
    message: string
    color?: string
}>()
</script>
<style scoped>
button {
    font-family: "IntegralCF";
    font-size: 12px;
    font-weight: 400;
}
</style>