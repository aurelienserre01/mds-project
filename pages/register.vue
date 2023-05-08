<template>
    <div class="w-full h-screen flex p-5">
        <div class="left w-[50vw] h-full ">
            <NuxtLink to="/">
                <div class="mt-4 ml-4">
                    <div class="title">INFLINE</div>
                </div>
            </NuxtLink>
            <div class="w-[50%] m-auto my-20">
                <div>
                    <h3>S'inscrire</h3>
                    <div class="my-6">
                        <p>Tu es déjà inscrit ?</p>
                        <p>Tu peux <NuxtLink to="/login"><span class="text-purple">te connecter ici !</span></NuxtLink>
                        </p>
                    </div>
                </div>
                <div class="form">
                    <div class="email my-10">
                        <label for="email">email</label>
                        <div class="flex items-center justify-center border-b-2 border-black">
                            <img src="~/assets/images/login/email.svg" alt="">
                            <input
                                class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
                                placeholder="Entre ton adresse mail" type="email" name="email" id="email" v-model="email">
                        </div>
                    </div>
                    <div class="password my-10">
                        <label for="password">Mot de passe</label>
                        <div class="flex items-center justify-center border-b-2 border-black">
                            <img src="~/assets/images/login/password.svg" alt="">
                            <input
                                class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
                                placeholder="Entre ton mot de passe" :type="showPassword ? 'text' : 'password'"
                                name="password" id="password" v-model="password">
                            <img @click="showPassword = !showPassword" src="~/assets/images/login/eyes.svg" alt="">
                        </div>
                    </div>
                    <div class="password mb-2">
                        <label for="password">Confirmation de mot de passe</label>
                        <div class="flex items-center justify-center border-b-2 border-black">
                            <img src="~/assets/images/login/password.svg" alt="">
                            <input
                                class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
                                placeholder="Confirme ton mot de passe" :type="showPassword ? 'text' : 'password'"
                                name="password" id="password" v-model="passwordConfirm">
                            <img @click="showPassword = !showPassword" src="~/assets/images/login/eyes.svg" alt="">
                        </div>
                    </div>
                </div>
                <Button @click="register()" class="my-12" message="S'inscrire" color="purple" />
            </div>
        </div>
        <div class="bg-black w-[50vw] rounded-2xl p-3">
            <div class="text-white flex justify-end items-center">
                <img class="mr-2" src="~/assets/images/login/phone-call.svg" alt="">
                <span class="phone">+94 0116 789 754</span>
            </div>
            <div class="min-h-[456px] mt-16">
                <img class="rounded-[232px] ml-auto mr-auto h-[456px] w-[312px] object-cover"
                    src="~/assets/images/femme_selfie.png">
            </div>
            <div class="desc ml-20 mt-20 text-white">
                <span class="communaute">Rejoins la communauté</span><br />
                Et sois mis en relation en 15 secondes
            </div>

        </div>
    </div>
</template>
<script setup lang="ts">
import Button from '~/components/shared/Button.vue';
import axios from 'axios';
const showPassword = ref(false);
const success = ref(true);
const email = ref('');
const password = ref('');
const passwordConfirm = ref('');
const userModel = ref({})


async function register() {
    if (email.value != '' && password.value != '' && passwordConfirm.value != '') {
        try {
            const response = await axios.post('http://localhost:1337/api/auth/local/register', { username: email.value, email: email.value, password: password.value });
            storeLoggedInUser(response.data)
        } catch (error) {
            success.value = false
        }
    } else {
        success.value = false
    }

    if (success.value) {
        navigateTo('/map')
    }
}
function storeLoggedInUser(user: any) {
    userModel.value = user;
    window.localStorage.setItem('rememberMe', JSON.stringify(user));
}
</script>
<style scoped>
.communaute {
    font-family: "Poppins";
    font-weight: 600;
    font-size: 2vw;
}

.phone {
    font-family: "Poppins";
    font-weight: 500;
    font-size: 0.8vw;
}

.desc {
    font-family: "Poppins";
    font-weight: lighter;
    font-size: 1vw;
    line-height: 2.5vw;
}

.title {
    font-family: "IntegralCF";
    font-weight: 600;
    font-size: 24px;
}

h3 {
    font-family: "IntegralCF";
    font-weight: 600;
    font-size: 30px;
}

label {
    font-family: "Poppins";
    color: #999999;
    font-size: 13px;
}

.password-forget {
    font-family: "Poppins";
    color: #999999;
    font-size: 13px;
}

.continue {
    font-family: "Poppins";
    color: #999999;
    font-size: 14px;
}
</style>