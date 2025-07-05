<script setup>
  const color = "red"

</script>

<template>
<header>Лого</header>
<main :class="color">Основной контент</main>
</template>

<style scoped>
.red {
  color: red;
}
</style>
