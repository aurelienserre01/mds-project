<template>
    <div class="bg-white">
        <div class="pl-20 pt-16 pb-16">
            <div>
                <h4>Les news</h4>
            </div>
            <div class="flex justify-around mt-10">
                <Blog date="4 mars 2022" message="Trouver l'inflenceur parfait pour votre marque" img="femme_selfie.png" :important=false />
                <Blog date="7 mars 2022" message="50 nouvelles influenceuses rejoigent la plateforme" img="femme_selfie.png" :important=true />
                <Blog date="1 juin 2022" message="Instagram investit 100 millions d’euros dans Infline" img="femme_selfie.png" :important=false />
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">

import Blog from './shared/Blog.vue';
</script>
<style scoped>
h4 {
    font-weight: 800;
    font-size: 3vw;
    font-family: "IntegralCF";
}


</style>