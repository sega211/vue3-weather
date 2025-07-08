<script setup>
import { computed } from 'vue';
import IconSun from "../icons/weather/IconSun.vue";
import IconRain from "../icons/weather/IconRain.vue";
import IconCloud from "../icons/weather/IconCloud.vue";
import IconSnow from "../icons/weather/IconSnow.vue";

const props = defineProps({
    dayData: Object,
    city: String
});

// Определяем тип погоды для иконки
const weatherType = computed(() => {
    if (!props.dayData) return 'sun';
    const code = props.dayData.day.condition.code;
    
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

    if (sunnyCodes.includes(code)) return 'sun';
    if (cloudyCodes.includes(code)) return 'cloud';
    if (rainCodes.includes(code)) return 'rain';
    if (snowCodes.includes(code)) return 'snow';
    
    return 'sun';
});

// Форматируем дату
const formattedDate = computed(() => {
    if (!props.dayData) return '';
    const date = new Date(props.dayData.date);
    return date.toLocaleDateString('ru-RU', {
        day: 'numeric',
        month: 'long'
    });
});

// Форматируем день недели
const dayOfWeek = computed(() => {
    if (!props.dayData) return '';
    const date = new Date(props.dayData.date);
    return date.toLocaleDateString('ru-RU', {
        weekday: 'long'
    });
});
</script>

<template>
    <div v-if="dayData" class="pane-left">
        <div class="pane-left__header">
            <div class="header-item">{{ dayOfWeek }}</div>
            <div class="header-item">{{ formattedDate }}</div>
            <div class="header-item">{{ city }}</div>
        </div>
        
        <div class="pane-left__main">
            <div class="weather-icon">
                <IconSun v-if="weatherType === 'sun'" color="#FFD700" :size="100" />
                <IconCloud v-if="weatherType === 'cloud'" color="#FFFFFF" :size="100" />
                <IconRain v-if="weatherType === 'rain'" color="#1E90FF" :size="100" />
                <IconSnow v-if="weatherType === 'snow'" color="#FFFFFF" :size="100" />
            </div>
            <div class="temperature">{{ Math.round(dayData.day.avgtemp_c) }}°C</div>
            <div class="condition">{{ dayData.day.condition.text }}</div>
            
            <!-- Блок с максимальной и минимальной температурой -->
            <div class="temp-range">
                <div class="temp-high">
                    <span class="label">Макс:</span>
                    <span class="value">{{ Math.round(dayData.day.maxtemp_c) }}°</span>
                </div>
                <div class="temp-divider"></div>
                <div class="temp-low">
                    <span class="label">Мин:</span>
                    <span class="value">{{ Math.round(dayData.day.mintemp_c) }}°</span>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.pane-left {
    display: flex;
    flex-direction: column;
    height: 100%;
    padding: 40px;
    color: white;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
    box-sizing: border-box;
    position: relative;
    z-index: 1;
}

.pane-left__header {
    display: flex;
    justify-content: space-between;
    font-size: 18px;
    margin-bottom: 60px;
}

.header-item {
    background: rgba(50, 120, 70, 0.4);
    padding: 8px 16px;
    border-radius: 20px;
    backdrop-filter: blur(4px);
    border: 1px solid rgba(255, 255, 255, 0.2);
}

.pane-left__main {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 50px;
    padding: 30px;
    background: rgba(30, 70, 40, 0.3);
    border-radius: 20px;
    backdrop-filter: blur(5px);
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.weather-icon {
    margin-bottom: 20px;
    filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.3));
}

.temperature {
    font-size: 80px;
    font-weight: bold;
    margin: 20px 0;
    line-height: 1;
    color: #e0ffe0;
}

.condition {
    font-size: 24px;
    text-align: center;
    max-width: 80%;
    color: #d0f0d0;
    margin-bottom: 30px;
}

/* Стили для блока температур */
.temp-range {
    display: flex;
    align-items: center;
    gap: 20px;
    background: rgba(40, 100, 60, 0.4);
    padding: 15px 25px;
    border-radius: 15px;
    backdrop-filter: blur(3px);
    border: 1px solid rgba(255, 255, 255, 0.15);
}

.temp-high, .temp-low {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.label {
    font-size: 16px;
    opacity: 0.8;
    margin-bottom: 5px;
}

.value {
    font-size: 24px;
    font-weight: bold;
}

.temp-divider {
    width: 1px;
    height: 40px;
    background: rgba(255, 255, 255, 0.3);
}
</style>