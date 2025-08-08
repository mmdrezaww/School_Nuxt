<template>
  <header class="bg-white shadow-lg sticky top-0 z-50">
    <!-- Top Contact Bar -->
    <div class="bg-blue-900 text-white py-2">
      <div class="container mx-auto px-4">
        <div class="flex justify-between items-center text-sm">
          <div class="flex items-center space-x-4 space-x-reverse">
            <span class="flex items-center">
              <svg class="w-4 h-4 ml-2" fill="currentColor" viewBox="0 0 20 20">
                <path d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z"></path>
                <path d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z"></path>
              </svg>
              info@rahmanischool.ir
            </span>
            <span class="flex items-center">
              <svg class="w-4 h-4 ml-2" fill="currentColor" viewBox="0 0 20 20">
                <path d="M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z"></path>
              </svg>
              ۰۲۶-۳۲۱۲۳۴۵۶
            </span>
          </div>
          <div class="flex items-center space-x-3 space-x-reverse">
            <span>مدرسه دخترانه رحمانی - کرج</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Main Header -->
    <div class="container mx-auto px-4">
      <div class="flex justify-between items-center py-4">
        <!-- Logo -->
        <div class="flex items-center">
          <div class="bg-blue-900 text-white p-3 rounded-lg ml-4">
            <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 20 20">
              <path d="M10.394 2.08a1 1 0 00-.788 0l-7 3a1 1 0 000 1.84L5.25 8.051a.999.999 0 01.356-.257l4-1.714a1 1 0 11.788 1.838L7.667 9.088l1.94.831a1 1 0 00.787 0l7-3a1 1 0 000-1.838l-7-3zM3.31 9.397L5 10.12v4.102a8.969 8.969 0 00-1.05-.174 1 1 0 01-.89-.89 11.115 11.115 0 01.25-3.762zM9.3 16.573A9.026 9.026 0 007 14.935v-3.957l1.818.78a3 3 0 002.364 0l5.508-2.361a11.026 11.026 0 01.25 3.762 1 1 0 01-.89.89 8.968 8.968 0 00-5.35 2.524 1 1 0 01-1.4 0zM6 18a1 1 0 001-1v-2.065a8.935 8.935 0 00-2-.712V17a1 1 0 001 1z"></path>
            </svg>
          </div>
          <div>
            <h1 class="text-2xl font-bold text-blue-900">مجتمع آموزشی رحمانی</h1>
            <p class="text-gray-600 text-sm">تربیت نسلی متعهد و دانشمند</p>
          </div>
        </div>

        <!-- Desktop Navigation -->
        <nav class="hidden lg:flex items-center space-x-8 space-x-reverse">
          <NuxtLink to="/" class="nav-link">خانه</NuxtLink>
          <NuxtLink to="/about" class="nav-link">درباره ما</NuxtLink>
          <NuxtLink to="/services" class="nav-link">خدمات آموزشی</NuxtLink>
          <NuxtLink to="/gallery" class="nav-link">گالری تصاویر</NuxtLink>
          <NuxtLink to="/news" class="nav-link">اخبار</NuxtLink>
          <NuxtLink to="/contact" class="nav-link">تماس با ما</NuxtLink>
        </nav>

        <!-- Mobile Menu Button -->
        <button
            @click="toggleMobileMenu"
            class="lg:hidden p-2 rounded-md text-blue-900 hover:bg-blue-50"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div
        v-show="isMobileMenuOpen"
        class="lg:hidden bg-white border-t shadow-lg"
    >
      <nav class="container mx-auto px-4 py-4 space-y-3">
        <NuxtLink to="/" class="mobile-nav-link">خانه</NuxtLink>
        <NuxtLink to="/about" class="mobile-nav-link">درباره ما</NuxtLink>
        <NuxtLink to="/services" class="mobile-nav-link">خدمات آموزشی</NuxtLink>
        <NuxtLink to="/gallery" class="mobile-nav-link">گالری تصاویر</NuxtLink>
        <NuxtLink to="/news" class="mobile-nav-link">اخبار</NuxtLink>
        <NuxtLink to="/contact" class="mobile-nav-link">تماس با ما</NuxtLink>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}
</script>

<style scoped>
.nav-link {
  @apply text-gray-700 hover:text-blue-900 font-medium transition-colors duration-200 py-2 px-3 rounded-md hover:bg-blue-50;
}

.mobile-nav-link {
  @apply block text-gray-700 hover:text-blue-900 font-medium py-3 px-4 rounded-md hover:bg-blue-50 transition-colors duration-200;
}

.router-link-active {
  @apply text-blue-900 bg-blue-50;
}
</style>