<template>
  <nav class="bg-white/90 backdrop-blur-md shadow-sm sticky top-0 z-50 border-b border-gray-100" dir="rtl">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        <!-- بخش راست (لوگو + منو) -->
        <div class="flex items-center">
          <!-- لوگو -->
          <div class="flex-shrink-0 flex items-center">
            <svg class="h-10 w-10 text-indigo-600" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 6.253V19.5a.75.75 0 01-1.075.676l-6.5-3.5a.75.75 0 010-1.352l6.5-3.5A.75.75 0 0112 6.253zM12.825 6.253a.75.75 0 011.075-.676l6.5 3.5a.75.75 0 010 1.352l-6.5 3.5a.75.75 0 01-1.075-.676V6.253zM11.25 3a.75.75 0 01.75-.75h7.5a.75.75 0 01.75.75v3a.75.75 0 01-.75.75h-7.5a.75.75 0 01-.75-.75v-3zM4.25 12a.75.75 0 01.75-.75h7.5a.75.75 0 01.75.75v3a.75.75 0 01-.75.75h-7.5a.75.75 0 01-.75-.75v-3z"/>
            </svg>
            <span class="text-2xl font-bold text-gray-900 mr-3">مدرسه رحمانی</span>
          </div>

          <!-- منوی دسکتاپ -->
          <div class="hidden md:block mr-10">
            <div class="flex items-baseline space-x-6 space-x-reverse">
              <NuxtLink
                  v-for="item in navigation"
                  :key="item.name"
                  :to="item.href"
                  class="px-4 py-2 rounded-lg text-base font-medium hover:bg-gray-100/50 transition-all flex items-center"
                  :class="item.current ? 'text-indigo-600 bg-gray-100/30 font-semibold' : 'text-gray-700 hover:text-indigo-500'"
              >
                <span class="ml-2" v-html="item.icon"></span>
                {{ item.name }}
              </NuxtLink>
            </div>
          </div>
        </div>

        <!-- بخش چپ (ورود + ثبت نام) -->
        <div class="hidden md:block">
          <div class="flex items-center space-x-4 space-x-reverse">
            <!-- دکمه ثبت نام -->
            <NuxtLink
                to="/register"
                class="px-5 py-2.5 text-base font-medium text-white bg-indigo-600 rounded-lg hover:bg-indigo-700 transition flex items-center shadow-lg hover:shadow-indigo-200"
            >
              <svg class="h-5 w-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18 9v3m0 0v3m0-3h3m-3 0h-3m-2-5a4 4 0 11-8 0 4 4 0 018 0zM3 20a6 6 0 0112 0v1H3v-1z"/>
              </svg>
              ثبت نام
            </NuxtLink>
            <!-- دکمه ورود -->
            <NuxtLink
                to="/login"
                class="px-5 py-2.5 text-base font-medium text-indigo-600 hover:text-indigo-800 transition flex items-center border border-indigo-600 rounded-lg hover:bg-indigo-50"
            >
              <svg class="h-5 w-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 16l-4-4m0 0l4-4m-4 4h14m-5 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h7a3 3 0 013 3v1"/>
              </svg>
              ورود
            </NuxtLink>
          </div>
        </div>

        <!-- منوی موبایل -->
        <div class="md:hidden flex items-center">
          <button
              @click="isOpen = !isOpen"
              class="inline-flex items-center justify-center p-2 rounded-md text-gray-700 hover:text-indigo-500 focus:outline-none"
          >
            <svg class="h-8 w-8" :class="{'hidden': isOpen, 'block': !isOpen}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
            </svg>
            <svg class="h-8 w-8" :class="{'hidden': !isOpen, 'block': isOpen}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- منوی موبایل (کشویی) -->
    <div class="md:hidden" :class="{'block': isOpen, 'hidden': !isOpen}">
      <div class="px-2 pt-2 pb-3 space-y-2 sm:px-3 bg-white/95 backdrop-blur-sm">
        <NuxtLink
            v-for="item in navigation"
            :key="item.name"
            :to="item.href"
            class="block px-4 py-3 rounded-lg text-base font-medium flex items-center"
            :class="item.current ? 'text-indigo-600 bg-gray-100/30' : 'text-gray-700 hover:text-indigo-500 hover:bg-gray-100/50'"
            @click="isOpen = false"
        >
          <span class="ml-2" v-html="item.icon"></span>
          {{ item.name }}
        </NuxtLink>

        <div class="pt-4 border-t border-gray-200 space-y-3">
          <NuxtLink
              to="/login"
              class="block w-full px-4 py-3 text-center text-indigo-600 border border-indigo-600 rounded-lg hover:bg-indigo-50 transition flex items-center justify-center"
          >
            <svg class="h-5 w-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 16l-4-4m0 0l4-4m-4 4h14m-5 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h7a3 3 0 013 3v1"/>
            </svg>
            ورود
          </NuxtLink>
          <NuxtLink
              to="/register"
              class="block w-full px-4 py-3 text-center text-white bg-indigo-600 rounded-lg hover:bg-indigo-700 transition flex items-center justify-center"
          >
            <svg class="h-5 w-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18 9v3m0 0v3m0-3h3m-3 0h-3m-2-5a4 4 0 11-8 0 4 4 0 018 0zM3 20a6 6 0 0112 0v1H3v-1z"/>
            </svg>
            ثبت نام
          </NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
const isOpen = ref(false)

const navigation = [
  {
    name: 'خانه',
    href: '/',
    current: true,
    icon: `<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"/>
          </svg>`
  },
  {
    name: 'درباره ما',
    href: '/about',
    current: false,
    icon: `<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
          </svg>`
  },
  {
    name: 'پیش‌دبستانی',
    href: '/preschool',
    current: false,
    icon: `<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/>
          </svg>`
  },
  {
    name: 'دبستان',
    href: '/elementary',
    current: false,
    icon: `<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2"/>
          </svg>`
  },
  {
    name: 'تماس با ما',
    href: '/contact',
    current: false,
    icon: `<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
          </svg>`
  },
]
</script>

<style scoped>
/* پشتیبانی از فونت فارسی (بدون نیاز به پکیج) */
body {
  font-family: Tahoma, Arial, sans-serif;
}

/* انیمیشن‌های سفارشی */
.router-link-active {
  position: relative;
}
.router-link-active::after {
  content: '';
  position: absolute;
  bottom: -4px;
  right: 50%;
  transform: translateX(50%);
  width: 60%;
  height: 3px;
  background: #4f46e5;
  border-radius: 3px;
}

/* اصلاح جهت‌ها برای RTL */
[dir="rtl"] .space-x-reverse > :not([hidden]) ~ :not([hidden]) {
  margin-right: 0.5rem;
  margin-left: 0;
}

/* افکت سایه برای دکمه ثبت نام */
.hover\:shadow-indigo-200:hover {
  --tw-shadow: 0 4px 6px -1px rgba(199, 210, 254, 0.5), 0 2px 4px -1px rgba(199, 210, 254, 0.5);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}
</style>