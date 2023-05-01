<template>
    <div class="w-screen h-screen p-9">
        <div class="left w-[50vw]">
            <div class="mt-4">
                <div class="title">INFLINE</div>
            </div>
        </div>
        <div class="mt-6">
            <div class="hello">HELLO,</div>
            <div>Trouve l'influenceur qu'il te faut ici !</div>
        </div>
        <div id="mapContainer" class="w-[70%] h-[60vh] my-10 rounded-full "></div>
    </div>
</template>
<script setup lang="ts">
import mapboxgl, { Map, type LngLatLike } from "mapbox-gl";
</script>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    data() {
        return {
            map: {} as Map,
            longitudeLatitudeEdit: {} as LngLatLike,
            accessToken: "pk.eyJ1IjoiYXVyZWxpZW4wMSIsImEiOiJjbGg1MDRicXowM2ptM3JzOHRuajl0ZnBwIn0.dUwRt2SK7CNKE2zSKaCktQ",
        };
    },
    methods: {

    },
    mounted() {
        mapboxgl.accessToken = this.accessToken;
        this.map = new mapboxgl.Map({
            accessToken:
                "pk.eyJ1IjoiYXVyZWxpZW4wMSIsImEiOiJjbGg1MDRicXowM2ptM3JzOHRuajl0ZnBwIn0.dUwRt2SK7CNKE2zSKaCktQ",
            container: "mapContainer",
            style: "mapbox://styles/mapbox/light-v11",
            center: [6.11667, 45.900002],
            zoom: 12,
        });
    },
})

</script>
<style scoped>
.title {
    font-family: "IntegralCF";
    font-weight: 600;
    font-size: 24px;
}

.hello{
    font-family: "IntegralCF";
    font-weight: 600;
    font-size: 30px;
}
</style>