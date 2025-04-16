<template>
  <div>
    <h1>Course {{ id }}</h1>
  </div>
</template>

<script setup>
const { id } = useRoute().params
</script>

<style scoped>

</style>
