<script setup>
import Error from "../../components/Error/Error.vue";
import CardDay from "../../components/Cards/CardDay.vue";
import Stat from "../../components/Stat/Stat.vue";
import CitySelect from "../../components/CitySelect.vue";
import { computed } from "vue";
import { errorMap } from "../../constants";

const { error, data, activeIndex } = defineProps({
    error: Object,
    data: Object,
    activeIndex: Number
});

const emit = defineEmits(["select-index", "select-city"]);

const statData = computed(() => {
    if (!data || activeIndex === undefined) return;
    
    // Получаем данные для выбранного дня
    const dayData = data.forecast.forecastday[activeIndex];
    
    // Для текущего дня используем актуальные данные, для остальных - прогнозные
    const isCurrentDay = activeIndex === 0;
    
    return [
        {
            label: "Влажность",
            stat: (isCurrentDay ? data.current.humidity : dayData.day.avghumidity) + " %"
        },
        {
            label: "Облачность",
            stat: (isCurrentDay ? data.current.cloud : dayData.day.avgvis_km) + " %"
        },
        {
            label: "Ветер",
            stat: (isCurrentDay ? data.current.wind_kph : dayData.day.maxwind_kph) + " км/ч"
        }
    ];
});

const errorDisplay = computed(() => {
    return errorMap.get(error?.error?.code);
});
</script>

<template>
    <Error v-if="error" :error="errorDisplay"/>
    <div v-if="data" class="stat-data">
        <div class="stat-list">
            <Stat v-for="item in statData" v-bind="item" :key="item.label"/>
        </div>
        <div class="day-cards">
            <CardDay 
                v-for="(item, i) in data.forecast.forecastday" 
                :key="item.date"      
                :weather-code="item.day.condition.code" 
                :temperature="item.day.avgtemp_c" 
                :date="new Date(item.date)"
                :is-active="activeIndex === i"
                @click="() => emit('select-index', i)"
            />
        </div>
    </div>
    <CitySelect @select-city="(selectedCity) => emit('select-city', selectedCity)"/>
</template>

<style scoped>
.stat-data {
  display: flex;
  flex-direction: column;
  gap: 80px;
  margin-bottom: 70px;
}
.stat-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
  
}
.day-cards {
  display: flex;
  justify-content: center;
  gap:1px;
  
}
</style>