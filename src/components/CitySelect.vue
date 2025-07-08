<script setup>
    import {   inject, ref } from "vue";
    import Button from "./Button/Button.vue";
    import IconComponent from "./icons/IconLocation.vue";
    import Input from "./Input/Input.vue";
    import { cityProvide } from "../constants";

    const city = inject(cityProvide);
    const inputValue = ref(city.value)

    

 
    
    let isEdited = ref(false);

 

    function select() {
        isEdited.value = false
        city.value = inputValue.value
        // emit('selectCity', city.value)
        
    }
    function edit() {
        isEdited.value = true
    }

 
    
  
    

</script>
<template>
      
    
    <div class="city-select">
        
        <div v-if="isEdited" class="city-input">
        <Input  
        v-model="inputValue" 
        v-focus="vFocus"
        placeholder="Введите название города" 
        
        @keyup.enter="select()"
        />
        <Button @click="select()">
            Сохранить
        </Button>  
    </div>
   <Button v-else @click="edit()">
      <IconComponent size="20px"/>
      Изменить город
    </Button> 
    </div>
      
 
</template>
<style scoped>
    .city-select {
         width:420px;
    }
        
    .city-input {
        display: flex;
        gap: 12px;
       
    }
</style>