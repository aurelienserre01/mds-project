<template>
    <div class="homeHero bg-black h-screen">
        <div class="header text-white uppercase text-center pt-4">
            infline
        </div>
        <div class=" grid auto-rows-auto grid-flow-col max-w-[90%] ml-auto mr-auto">
            <div class="pl-20">
                <div class="w-[65%] titre text-white mt-36 items-center">
                    <h1>La platemforme n°1 pour trouver un <span class="wordart text-black">influenceur</span></h1>
                </div>
                <div class="buttons mt-16 pb-32">
                    <SharedButton class="mr-8" message="Je suis influenceur" />
                    <SharedButton message="Je suis une marque" color="purple" />
                </div>
            </div>
            <div class=" image mt-auto pt-28 pr-16">
                <img src="~/assets/images/femme_selfie.png" alt="Femme prenant un selfie">
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
    font-size: 55px;
    line-height: 72px;
}
</style>