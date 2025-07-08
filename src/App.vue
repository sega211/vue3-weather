<script setup>
 
  import PaneRight from "./components/Panes/PaneRight.vue";
  import PaneLeft from "./components/Panes/PaneLeft.vue";
  import {  onMounted, provide, ref, watch } from "vue";
  import { API_ENDPOINT, cityProvide } from "./constants";

  
  let data = ref()
  let error = ref();
  let activeIndex = ref(0)
  let city = ref("Пятигорск");

  provide(cityProvide, city)
  watch(city, () => {
    getCity(city.value)
  })

  onMounted(() => {
    getCity(city.value)
  })
  
  
  async function getCity(city) {
    const params = new URLSearchParams({
      q: city,
      lang: "ru",
      days: 3,
      key:'031b3e4e7b41486eb5264718250707',

    })
    const res = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`);
    if (res.status !== 200) {
      error.value = await res.json();
      data.value = null;
      return;
    }
    error.value = null;
   data.value = await res.json()
  }
</script>

<template>
  <main class="main">
    <div class="left">
      <PaneLeft 
      :dayData="data?.forecast.forecastday[activeIndex]"
      :city="city"
      />
    </div>
    <div class="right">
      <PaneRight  
      :data
      :error
      :active-index="activeIndex" 
      @select-index="(i) => (activeIndex = i)"
      
       />
    </div>
  </main>
 


</template>

<style scoped>
.main {
  display: flex;
  align-items: center;
  justify-content: center;
}
.left {
  background: 
    linear-gradient(135deg, rgba(40, 100, 60, 0.6) 0%, rgba(30, 80, 50, 0.4) 100%),
    url('../public/nature.jpg') no-repeat center center;
  background-size: cover;
  background-blend-mode: overlay;
  width: 500px;
  height: 660px;
  border-radius: 30px;
  position: relative;
  overflow: hidden;
}

.left::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: inherit;
  filter: blur(8px);
  z-index: -1;
  margin: -10px; /* Увеличиваем область для размытия краев */
}
.right {
  background: var(--color-bg-main);
  padding: 60px 50px;
  border-radius: 25px;
}


  </style>