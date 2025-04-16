<template>
  <div>
    <h1>
      {{ id }}
    </h1>
  </div>
</template>

<script setup>
const route = useRoute()
const id = computed(() => route.params.id)
</script>

<style scoped>

</style>
