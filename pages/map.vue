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
        <Popup
            description="Hello, moi c’est Marie, 24 ans. Je suis influenceuse beauté depuis plus de 3 ans, spécialiste Insta et TikTok"
            nom="Marie, influenceuse beauté" />

        <Button color="purple" message="Rechercher ici" />
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
    response.data.data.forEach((element: { attributes: { name: string; description: string; longitude: any; latitude: any; }; }) => {
        let marker = document.createElement('div');
        marker.className = 'marker';
        marker.setAttribute('style', 'width: 20px;height: 20px;border-radius: 10px;background: #B188EA;')
        const popup = new mapboxgl.Popup({ closeButton: false, offset: 50 }).setHTML('<div> Nom : ' + element.attributes.name + ' </div> <div> Description : ' + element.attributes.description + ' </div>');
        new mapboxgl.Marker(marker).setLngLat([Number(element.attributes.longitude), Number(element.attributes.latitude)]).setPopup(popup).addTo(map);
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

.mapboxgl-popup-content {
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
    width: 40px;
    height: 40px;
    border-radius: 20px;
    background: green;
}
</style>