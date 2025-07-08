<script setup>
import IconSun from "../icons/weather/IconSun.vue";
import IconRain from "../icons/weather/IconRain.vue";
import IconCloud from "../icons/weather/IconCloud.vue";
import IconSnow from "../icons/weather/IconSnow.vue";
import { computed } from "vue";



    const {weatherCode, temperature, date} = defineProps({
        weatherCode: Number,
        temperature: Number,
        date: Date,
        isActive: Boolean
    })
    // Группировка кодов погоды по типам
const weatherTypes = computed(() => {
    const sunnyCodes = [1000];
    const cloudyCodes = [1003, 1006, 1009, 1030, 1135, 1147];
    const rainCodes = [
        1063, 1072, 1150, 1153, 1168, 1171, 1180, 1183, 1186, 
        1189, 1192, 1195, 1198, 1201, 1240, 1243, 1246, 1249, 
        1252, 1261, 1264, 1273, 1276
    ];
    const snowCodes = [
        1066, 1069, 1114, 1117, 1204, 1207, 1210, 1213, 
        1216, 1219, 1222, 1225, 1237, 1255, 1258, 1264, 
        1279, 1282
    ];

    if (sunnyCodes.includes(weatherCode)) return 'sun'
    if (cloudyCodes.includes(weatherCode)) return 'cloud'
    if (rainCodes.includes(weatherCode)) return 'rain'
    if (snowCodes.includes(weatherCode)) return 'snow'
    
    return 'sun' // значение по умолчанию
})
</script>

<template>
    <button class="day-card" :class="{ 'active': isActive }">
    <IconSun v-if="weatherTypes === 'sun'" :color="'#FFD700'" :size="54" />
        <IconCloud v-if="weatherTypes === 'cloud'" :color="'#A9A9A9'" :size="54" />
        <IconRain v-if="weatherTypes === 'rain'" :color="'#1E90FF'" :size="54" />
        <IconSnow v-if="weatherTypes === 'snow'" :color="'#FFFFFF'" :size="54" />
        <div class="day-card__date">
            {{ date.toLocaleDateString("ru-RU", { weekday: "short" }) }}
        </div>
        <div class="day-card__temperature">
            {{ Math.round( temperature) }}°C
        </div>
    </button>
</template>

<style  scoped>
    .day-card {
        width: 100%;
        border: none;
        border-radius: 10px;
        box-shadow: 1px 2px 4px 0px var(--color-bg-main);
        color: var(--color-primary);
        padding: 20px 24px;
        background-color: var(--color-bg-card);
        display: flex;
        flex-direction: column;
        align-items: center;;
        justify-content: center;
        gap:15px;
        cursor: pointer;
    }
    .day-card:hover {
        background-color: #3a434f;
    }
    .active {
        background-color: var(--color-primary);
        color:var(--color-primary-inverted);
    }
    .day-card__date {
        font-size: 20px;
       
       
    }
    .day-card__temperature {
        font-size: 20px;
        
        font-weight: 700;
    }

</style>