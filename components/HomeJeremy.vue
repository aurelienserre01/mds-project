<template>
    <div class="bg-black ">
        <div class="flex pt-28 pb-28 items-center justify-center">
            <img width="458" height="493" class="translate-x-[7%]" src="~/assets/images/influenceur.jpg" alt="" srcset="">
            <div class="bg-white w-1/3 h-fit -translate-x-[7%]">
                <div class="p-[50px]">
                    <div class="title mb-4">Jérôme, influenceur sport</div>
                    <div class="description mb-4">Infline m’a permis d’être en relation avec plus de 100 marques depuis que
                        je me suis inscrit sur la
                        plateforme. C’est de la bombe !</div>
                    <Button message="Voir les autres avis" color="purple" />
                </div>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import Button from './shared/Button.vue';

</script>
<style scoped>
.title {
    font-family: "poppins";
    font-weight: 800;
    font-size: 24px;

}

.description {
    font-family: "poppins";
    font-weight: 500;
    font-size: 24px;
}
</style>