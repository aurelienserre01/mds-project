<template>
    <div class="w-screen h-screen p-9">
        <div class="left w-[50vw]">
            <NuxtLink to="/">
                <div class="mt-4">
                    <div class="title">INFLINE</div>
                </div>
            </NuxtLink>
        </div>
        <div class="mt-6">
            <div class="hello">HELLO,</div>
            <div>Trouve l'influenceur qu'il te faut ici !</div>
        </div>
        <div id="mapContainer" class="w-[70%] h-[60vh] my-10 rounded-2xl"></div>
        
    </div>
</template>
<script setup lang="ts">
import axios from "axios";
import mapboxgl, { Map, type LngLatLike } from "mapbox-gl";
import 'mapbox-gl/dist/mapbox-gl.css';
import Button from "~~/components/shared/Button.vue";
import Popup from "~~/components/shared/Popup.vue";
let map = reactive({} as Map);
const accessToken = ref("pk.eyJ1IjoiYXVyZWxpZW4wMSIsImEiOiJjbGg1MDRicXowM2ptM3JzOHRuajl0ZnBwIn0.dUwRt2SK7CNKE2zSKaCktQ");
onMounted(() => {
    let userJson = reactive(retrieveUser())
    mapboxgl.accessToken = accessToken.value;

    map = new mapboxgl.Map({
        accessToken:
            "pk.eyJ1IjoiYXVyZWxpZW4wMSIsImEiOiJjbGg1MDRicXowM2ptM3JzOHRuajl0ZnBwIn0.dUwRt2SK7CNKE2zSKaCktQ",
        container: "mapContainer",
        style: "mapbox://styles/mapbox/light-v11",
        center: [6.11667, 45.900002],
        zoom: 12,
    });
    recupInfluenceur(userJson)
    // document.getElementsByClassName('mapboxgl-ctrl-attrib-inner')[0].setAttribute('style', 'display:none')

})

async function recupInfluenceur(user: any) {
    const response = await axios.get('http://localhost:1337/api/influenceurs', { headers: { Authorization: 'Bearer ' + user.jwt, 'Content-Type': 'application/json' } });
    console.log(response.data.data)
    response.data.data.forEach(element => {
        const popup = new mapboxgl.Popup({ offset: 50,className:'relative' }).setHTML('<div class="z-[100] w-[385px] h-[409px] bg-white rounded-lg shadow-lg"><div class="p-4"><img src="~/public/images/femme_selfie.png" alt="" width="350" height="200"class="object-cover rounded-lg w-[350px] h-[200px]"><h4 class="mt-4">Marie, influenceuse beauté</h4><p class="description-inf mt-3">Hello, moi c’est Marie, 24 ans. Je suis influenceuse beauté depuis plus de 3ans,spécialiste Insta et TikTok</p><div class="w-fit ml-auto mr-auto"><Button class=" mt-6" :message="'+ +'Contacter'+ +'" color="purple" /></div></div></div>');
        new mapboxgl.Marker({
            color: "#000000",
            draggable: false,
        }).setLngLat([Number(element.attributes.longitude), Number(element.attributes.latitude)]).setPopup(popup).addTo(map);
        console.log(map)
    });


}


function retrieveUser() {
    const user: string | null = window.localStorage.getItem('rememberMe');
    if (user) {
        return JSON.parse(user);
    } else {
        navigateTo('/')
    }
}
</script>
<style scoped>
.title {
    font-family: "IntegralCF";
    font-weight: 600;
    font-size: 24px;
}

.mapboxgl-popup-content{
    position: absolute;
    top: 200px;
    right: 200px;
    width: 500px;
    height: 300px;

}

.hello {
    font-family: "IntegralCF";
    font-weight: 600;
    font-size: 30px;
}

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
.marker {
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

</style>