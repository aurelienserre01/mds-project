<template>
    <div class="absolute w-[385px] top-64 right-72 h-[409px] bg-white rounded-lg shadow-lg">
        <div class="p-4">
            <img src="~/assets/images/femme_selfie.png" alt="" width="350" height="200"
                class='object-cover rounded-lg w-[350px] h-[200px]'>
            <h4 class="mt-4">{{nom}}</h4>
            <p class="description-inf mt-3">{{ description }}</p>
            <div class="w-fit ml-auto mr-auto">
                <Button class=" mt-6" :message="'Contacter'" color="purple" />
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import Button from "~~/components/shared/Button.vue";
defineProps<{
    description: string
    nom: string
}>()
</script>
<style scoped>
h4 {
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 800;
    font-size: 18px;
    line-height: 27px;
}

.description-inf {
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 21px;


}
</style>