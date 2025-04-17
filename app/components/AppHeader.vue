<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const route = useRoute()
const items = computed<NavigationMenuItem[]>(() => [
  {
    label: 'หน้าแรก',
    to: '/',
    active: route.path === '/'
  },
  {
    label: 'คอร์สทั้งหมด',
    to: '/courses',
    active: route.path.startsWith('/courses')
  },
  {
    label: 'ผู้สอน',
    to: '/teacher',
    active: route.path.startsWith('/teacher')
  },
  {
    label: 'ติดต่อเรา',
    to: '/contact',
    active: route.path.startsWith('/contact')
  },
  {
    label: 'บทความ',
    to: '/blog',
    active: route.path.startsWith('/blog')
  },
  {
    label: 'ค้นหา',
    icon: 'i-lucide-search',
    component: 'UInput',
    props: {
      placeholder: 'ค้นหาคอร์สเรียน...',
      color: 'gray',
      trailing: true,
      icon: 'i-lucide-search'
    }
  }
])
</script>

<template>
  <UHeader>
    <template #title>
      <LazyAppLogo class="h-6 w-auto" />
    </template>
    <UNavigationMenu :items="items" />
    <template #right>
      <UColorModeButton />
      <UButton
        to="/auth/login"
        icon="i-lucide-user"
      >
        เข้าสู่ระบบ
      </UButton>
      <UButton
        to="/auth/register"
        icon="i-lucide-user-plus"
      >
        สมัครสมาชิก
      </UButton>
    </template>
  </UHeader>
</template>
