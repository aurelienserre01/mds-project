<template>
    <div>
        <div class="text font-semibold pt-1 pb-1 border-b-2 border-black text-black">
            {{ date }}
        </div>
        <div class="text pt-3 pb-3">
            {{ message }}
        </div>
        <div v-if="important">
            <img :src="'/images/'+img" alt="">
        </div>
        <div v-if="!important" class="max-h-20">
            <img height="150" width="376" :src="'/images/'+img" alt="">
        </div>
    </div>
</template>
<script setup lang="ts">
defineProps<{
    date: string
    message: string
    img: string
    important: boolean
}>()
</script>
<style scoped>
.text{
    font-family: "Poppins";
    font-size: 16px;

}
</style>