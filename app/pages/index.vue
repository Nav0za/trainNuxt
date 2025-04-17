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
        <div
          v-for="review in reviews"
          :key="review.id"
          class="relative"
        >
          <UUser
            :name="review.title"
            class="border border-gray-200 rounded-lg p-4"
            :description="review.name"
            :avatar="{
              src: review.avatar
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
      <div class="flex justify-center flex-wrap gap-4">
        <UPageCard
          v-for="teacher in teachers"
          :key="teacher.id"
          :description="teacher.quote"
          class="w-60"
        >
          <template #header>
            <UUser
              v-bind="teacher.user"
            />
          </template>
          <div class="flex justify-center gap-2">
            <UButton
              to="/courses/teachers"
              class="w-full text-center"
              color="warning"
              variant="subtle"
              icon="i-heroicons-academic-cap"
            >
              ดูคอร์สของครู
            </UButton>
            <UButton
              to="/courses/teachers"
              class="w-full text-center"
              color="info"
              variant="subtle"
              icon="i-heroicons-user-circle"
            >
              ดูโปรไฟล์
            </UButton>
          </div>
        </UPageCard>
      </div>
    </section>
    <!-- promotion -->
    <section>
      <UPricingPlan
        title="แพ็คเกจพิเศษ"
        description="สมัครแพ็คเรียนเหมาทั้งหมวด"
        price="ลด 30%"
        class="max-w-md mx-auto my-10"
        :features="features"
      />
    </section>
    <!-- FAQ -->
    <section>
      <h2 class="text-3xl font-bold text-center mt-30 mb-10">
        คำถามที่พบบ่อย
      </h2>
      <div class="max-w-3xl mx-auto mb-20">
        <UPageAccordion :items="items" />
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({
  title: 'คอร์สออนไลน์',
  meta: [
    { name: 'description', content: 'คอร์สออนไลน์หลากหลายหมวด' }
  ]
})
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
const reviews = ref([
  {
    id: 1,
    title: 'เรียนเขียนนิยายที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!',
    name: 'แอน, นักเรียนจากคอร์ส #เขียนนิยาย',
    avatar: 'https://cdn.readawrite.com/articles/2190/2189569/thumbnail/large.gif?1'
  },
  {
    id: 2,
    title: 'เรียนเขียนโปรแกรมที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!',
    name: 'แอน, นักเรียนจากคอร์ส #เขียนโปรแกรม',
    avatar: 'https://s.isanook.com/ca/0/ud/277/1386777/istock-633114032.jpg?ip/resize/w728/q80/jpg'
  },
  {
    id: 3,
    title: 'เรียนวาดภาพดิจิทัลที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!',
    name: 'โทนี่, นักเรียนจากคอร์ส #วาดภาพดิจิทัล',
    avatar: 'https://st.depositphotos.com/1158045/2403/i/450/depositphotos_24036255-stock-photo-funny-face.jpg'
  },
  {
    id: 4,
    title: 'เรียนตัดต่อวิดีโอด้วยมือถือที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!',
    name: 'ลิซ่า, นักเรียนจากคอร์ส #ตัดต่อวิดีโอด้วยมือถือ',
    avatar: 'https://storage.thaipost.net/main/uploads/photos/big/20200717/image_big_5f1118f248d34.jpg'
  },
  {
    id: 5,
    title: 'เรียนธรรมะที่นี่แล้วเข้าใจง่ายมาก ไม่เคยคิดว่าจะเขียนจบ!',
    name: 'เบียร์, นักเรียนจากคอร์ส #การตื่นรู้ในธรรม',
    avatar: 'https://www.khaosod.co.th/wpapp/uploads/2024/10/5-7.jpg'
  }
])
const teachers = ref([
  {
    id: 1,
    user: {
      name: 'ครูจูน',
      description: 'นักเขียนมืออาชีพ',
      avatar: {
        src: 'https://s359.kapook.com/pagebuilder/f5c52236-d035-4d7d-b059-d82c47d3a655.jpg',
        alt: 'ครูจูน'
      }
    },
    quote: '"Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."'
  },
  {
    id: 2,
    user: {
      name: 'พี่บอส',
      description: 'ยูทูปเบอร์สายตัดต่อด้วยมือถือ',
      avatar: {
        src: 'https://static.thairath.co.th/media/4DQpjUtzLUwmJZZSGo1qfYXuPzzWtkNqnfTtoaplbU0V.jpg',
        alt: 'พี่บอส'
      }
    },
    quote: '"Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."'
  },
  {
    id: 3,
    user: {
      name: 'ครูเจน',
      description: 'ศิลปินดิจิทัลสายชิค',
      avatar: {
        src: 'https://s.isanook.com/jo/0/ud/492/2462673/jennie.jpg?ip/crop/w670h402/q80/jpg',
        alt: 'ครูเจน'
      }
    },
    quote: '"Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."'
  }
])
const features = ref([
  {
    title: 'สมัครวันนี้ แถมคลาส Mini Workshop ฟรี 1 คอร์ส',
    icon: 'i-heroicons-gift'
  }
])
const items = ref([
  {
    label: 'Lorem ipsum dolor sit elit. Quisquam, quos?',
    icon: 'i-lucide-circle-help',
    content: 'The transition to v3 involves significant changes, including new component structures, updated theming approaches, and revised TypeScript definitions. We recommend a careful, incremental upgrade process, starting with thorough testing in a development environment.'
  },
  {
    label: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos?',
    icon: 'i-lucide-circle-help',
    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos.'
  },
  {
    label: 'Lorem ipsum addicortion adipisicing elit. Quisquam, quos?',
    icon: 'i-lucide-circle-help',
    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos.'
  }
])
</script>

<style scoped></style>
