<template>
    <div class="homeHero z-40 bg-black min-h-screen">
        <NuxtLink to="/">
            <div class="header text-white uppercase text-center pt-4">
                infline
            </div>
        </NuxtLink>
        <div class="flex-row md:flex w-full mr-auto ml-auto">
            <div class="w-[100vw] md:w-[50vw]  ">
                <div class="titre text-white mt-6 md:mt-36 w-[650px] mx-auto text-center md:text-left">
                    <h1 class="">La platemforme n°1 pour trouver un <span class="wordart text-black">influenceur</span></h1>
                    <!-- <h1 class="md:text-5xl text-4xl">La platemforme n°1 pour trouver un <span class="wordart text-black">influenceur</span></h1> -->
                </div>
                <div v-if="user == null" class="buttons md:flex md:mt-16 md:pb-32 w-[650px] mx-auto">
                    <NuxtLink to="/login">
                        <SharedButton class="mr-8" message="Je suis influenceur" />
                    </NuxtLink>
                    <NuxtLink to="/login">
                        <SharedButton message="Je suis une marque" color="purple" />
                    </NuxtLink>
                </div>
                <div v-if="user" class="buttons md:flex md:mt-16 md:pb-32 w-[650px] mx-auto">
                    <NuxtLink to="/map">
                        <SharedButton class="mr-8" message="Je suis influenceur" />
                    </NuxtLink>
                    <NuxtLink to="/map">
                        <SharedButton message="Je suis une marque" color="purple" />
                    </NuxtLink>
                </div>
            </div>
            <div class="w-[100vw] md:w-[50vw] mt-[5vw] mb-0 image object-center z-40">
                <img class="mx-auto h-auto w-[60%]" src="~/assets/images/femme_selfie.png" alt="Femme prenant un selfie">
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const user = ref({})

onMounted(() => {
    user.value = retrieveUser();
})

function retrieveUser() {
  const user: string | null = window.localStorage.getItem('rememberMe');
  if (user) {
    return JSON.parse(user);
  } else {
    return null;
  }
}
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
}</style>