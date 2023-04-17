<template>
    <div class="homeHero z-40 bg-black min-h-screen">
        <div class="header text-white uppercase text-center pt-4">
            infline
        </div>
        <div class="flex-row md:flex w-full mr-auto ml-auto">
            <div class="w-[100vw] md:w-[50vw] ">
                <div class="titre text-white mt-6 md:mt-36 w-[500px] text-center md:text-left">
                    <h1 class="">La platemforme n°1 pour trouver un <span class="wordart text-black">influenceur</span></h1>
                    <!-- <h1 class="md:text-5xl text-4xl">La platemforme n°1 pour trouver un <span class="wordart text-black">influenceur</span></h1> -->
                </div>
                <div class="buttons md:flex md:mt-16 md:pb-32">
                    <SharedButton class="mr-8" message="Je suis influenceur" />
                    <SharedButton message="Je suis une marque" color="purple" />
                </div>
            </div>
            <div class="w-[100vw] md:w-[50vw] md:mt-32 image object-center mt-aut z-40">
                <img class="mr-auto ml-auto" src="~/assets/images/femme_selfie.png" alt="Femme prenant un selfie">
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
</script>

<style scoped>
.wordart {
    -webkit-text-stroke: 1px #B188EA;
}

.header {
    font-family: "IntegralCF";
    font-weight: 400;
    font-size: 24px;
}

h1 {
    font-family: "IntegralCF";
    font-weight: 600;
    line-height: 100%;
    font-size: 3vw;
}
</style>