<template>
  <div class="container mx-auto">
    <!-- pagehero -->
    <section>
      <UPageHero
        title="เรียนรู้ง่าย ได้ทักษะจริง กับคอร์สออนไลน์หลากหลายหมวด"
        description="เลือกเรียนตามสไตล์คุณ - ตั้งแต่เริ่มต้นจนมืออาชีพ"
        orientation="horizontal"
        :links="[
          {
            label: 'ดูคอร์สทั้งหมด!',
            to: '/courses'
          },
          {
            label: 'สมัครสมาชิกฟรี',
            to: '/register',
            variant: 'outline',
            color: 'warning',
            icon: 'i-heroicons-user-plus'
          }
        ]"
      >
        <img
          src="/images/heroImg.png"
          alt="App screenshot"
          class="rounded-lg shadow-2xl ring ring-(--ui-border)"
        >
      </UPageHero>
    </section>
    <!-- trending courses -->
    <section>
      <h2 class="text-3xl font-bold text-center mb-4">
        คอร์สเรียนยอดนิยม
      </h2>
      <UPageGrid>
        <UCard
          v-for="post in posts"
          :key="post.id"
          class="relative"
        >
          <UBadge
            color="success"
            variant="solid"
            class="absolute top-2 right-2"
          >
            ขายดี
          </UBadge>
          <img
            :src="post.image"
            class="w-full h-78 object-cover"
          >
          <template #footer>
            <h1 class="text-2xl font-bold">
              {{ post.title }}
            </h1>
            <p class="text-md text-gray-500">
              {{ post.description }}
            </p>
            <div class="flex items-center justify-between">
              <span class="text-3xl font-bold text-primary-600">
                ฿{{ post.price }}
              </span>
              <UButton
                :to="`/courses/${post.id}`"
                color="secondary"
                variant="subtle"
                icon="i-heroicons-arrow-up-right"
              >
                สมัครเรียน
              </UButton>
            </div>
          </template>
        </UCard>
      </UPageGrid>
    </section>
    <!-- categories -->
    <section>
      <h2 class="text-3xl font-bold text-center mt-30 mb-10">
        หมวดหมู่ของคอร์ส
      </h2>
      <div class="flex justify-center gap-2">
        <UButton
          v-for="category in categories"
          :key="category.id"
          variant="outline"
          color="secondary"
          :icon="category.icon"
          :to="`/courses/categories/${category.id}`"
        >
          {{ category.name }}
        </UButton>
      </div>
    </section>
    <!-- prominent points -->
    <section class="mt-30">
      <UPricingPlan
        title="ทำไมต้องเรียนกับเรา?"
        class="max-w-3xl mx-auto"
        :features="[
          'เรียนที่ไหนก็ได้ เมื่อไหร่ก็ได้',
          'สามารถเข้าถึงบทเรียนได้ตลอดชีวิต',
          'มีใบประกาศนียบัตร',
          'อัพเดทคอร์สใหม่ทุกเดือน'
        ]"
      />
    </section>
    <!-- reviews -->
    <section>
      <h2 class="text-3xl font-bold text-center mt-30 mb-10">
        รีวิวจากผู้เรียน
      </h2>
      <div class="flex justify-center gap-3 flex-wrap">
        <div class="relative">
          <UUser
            name="เรียนเขียนนิยายที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!"
            class="border border-gray-200 rounded-lg p-4"
            description="แอน, นักเรียนจากคอร์ส #เขียนนิยาย"
            :avatar="{
              src: 'https://cdn.readawrite.com/articles/2190/2189569/thumbnail/large.gif?1'
            }"
            chip
            size="xl"
          />
          <UBadge
            color="neutral"
            variant="soft"
            class="absolute bottom-2 right-2 text-yellow-400"
          >
            ★★★★★
          </UBadge>
        </div>
        <div class="relative">
          <UUser
            name="เรียนเขียนนิยายที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!"
            class="border border-gray-200 rounded-lg p-4"
            description="แอน, นักเรียนจากคอร์ส #เขียนนิยาย"
            :avatar="{
              src: 'https://s.isanook.com/ca/0/ud/277/1386777/istock-633114032.jpg?ip/resize/w728/q80/jpg'
            }"
            chip
            size="xl"
          />
          <UBadge
            color="neutral"
            variant="soft"
            class="absolute bottom-2 right-2 text-yellow-400"
          >
            ★★★★★
          </UBadge>
        </div>
        <div class="relative">
          <UUser
            name="เรียนเขียนนิยายที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!"
            class="border border-gray-200 rounded-lg p-4"
            description="แอน, นักเรียนจากคอร์ส #เขียนนิยาย"
            :avatar="{
              src: 'https://st.depositphotos.com/1158045/2403/i/450/depositphotos_24036255-stock-photo-funny-face.jpg'
            }"
            chip
            size="xl"
          />
          <UBadge
            color="neutral"
            variant="soft"
            class="absolute bottom-2 right-2 text-yellow-400"
          >
            ★★★★★
          </UBadge>
        </div>
      </div>
    </section>
    <!-- teacher recommendations -->
    <section>
      <h2 class="text-3xl font-bold text-center mt-30 mb-10">
        คอร์สของครูที่แนะนำ
      </h2>
    </section>
  </div>
</template>

<script setup>
const posts = ref([
  {
    id: 1,
    title: 'เริ่มเขียนนิยายใน 14 วัน',
    description: 'สำหรับมือใหม่ที่อยากเริ่มเขียนนิยาย',
    image: '/images/course-novel.png',
    to: '/courses/1',
    price: 990
  },
  {
    id: 2,
    title: 'ตัดต่อวิดีโอด้วยมือถือ',
    description: 'สำหรับมือใหม่ที่อยากเริ่มเขียนนิยาย',
    image: '/images/course-editing.png',
    to: '/courses/2',
    price: 790
  },
  {
    id: 3,
    title: 'วาดภาพดิจิทัลสำหรับมือใหม่',
    description: 'สำหรับมือใหม่ที่อยากเริ่มเขียนนิยาย',
    image: '/images/course-drawing.png',
    to: '/courses/3',
    price: 1290
  }
])
const categories = ref([
  {
    id: 1,
    name: 'การเขียน',
    icon: 'i-heroicons-pencil'
  },
  {
    id: 2,
    name: 'ศิลปะ & การออกแบบ',
    icon: 'i-heroicons-paint-brush'
  },
  {
    id: 3,
    name: 'วิดีโอ / คอนเทนต์',
    icon: 'i-heroicons-video-camera'
  },
  {
    id: 4,
    name: 'ทักษะการทำงาน',
    icon: 'i-heroicons-wrench'
  },
  {
    id: 5,
    name: 'พัฒนาตัวเอง',
    icon: 'i-heroicons-user-circle'
  }
])
</script>

<style scoped></style>
