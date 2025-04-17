<template>
  <UFooterColumns
    :columns="columns"
    class="border-t border-gray-200 p-5"
  >
    <template #right>
      <UButtonGroup
        orientation="horizontal"
        class="w-full"
      >
        <UButton
          class="w-full justify-center "
          color="neutral"
          variant="subtle"
          label="สมัครสมาชิก"
          icon="i-heroicons-user-plus"
          to="/auth/register"
        />
        <UButton
          class="w-full justify-center "
          color="neutral"
          variant="outline"
          label="เข้าสู่ระบบ"
          icon="i-heroicons-user"
          to="/auth/login"
        />
      </UButtonGroup>
    </template>
  </UFooterColumns>
</template>

<script setup lang="ts">
import type { FooterColumn } from '@nuxt/ui-pro'

const columns: FooterColumn[] = [
  {
    label: 'เมนู',
    children: [
      {
        label: 'คอร์สทั้งหมด',
        to: 'https://nuxters.nuxt.com',
        target: '_blank'
      },
      {
        label: 'ผู้สอน',
        to: 'https://masteringnuxt.com/nuxt3?ref=nuxt',
        target: '_blank'
      },
      {
        label: 'ติดต่อเรา',
        to: 'https://github.com/nuxt',
        target: '_blank'
      },
      {
        label: 'เงื่อนไขการใช้งาน',
        to: 'https://github.com/nuxt',
        target: '_blank'
      }
    ]
  },
  {
    label: 'ช่องทางติดต่อ',
    children: [
      {
        label: 'Facebook',
        to: 'https://content.nuxt.com/',
        target: '_blank'
      },
      {
        label: 'Line',
        to: 'https://devtools.nuxt.com/',
        target: '_blank',
      },
      {
        label: 'Email',
        to: 'https://image.nuxt.com/',
        target: '_blank'
      },
      {
        label: 'Instagram',
        to: 'https://ui.nuxt.com/',
        target: '_blank'
      }
    ]
  }
]
</script>
