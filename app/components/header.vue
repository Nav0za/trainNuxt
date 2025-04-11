<script setup lang="ts">
const route = useRoute()

const items = computed(() => [
  {
    label: 'Docs',
    to: '/getting-started',
    active: route.path.startsWith('/getting-started')
  },
  {
    label: 'Components',
    to: '/components',
    active: route.path.startsWith('/components')
  },
  {
    label: 'Roadmap',
    to: '/roadmap'
  },
  {
    label: 'Figma',
    to: 'https://www.figma.com/community/file/1288455405058138934',
    target: '_blank'
  },
  {
    label: 'Releases',
    to: 'https://github.com/nuxt/ui/releases',
    target: '_blank'
  }
])
</script>

<template>
  <UHeader>
    <template #title>
      <Logo class="h-6 w-auto" />
    </template>

    <UNavigationMenu :items="items" />

    <template #right>
      <UColorModeButton />

      
    </template>
  </UHeader>
</template>
