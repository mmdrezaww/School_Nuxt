<template>
  <div class="min-h-screen bg-gray-50" dir="rtl">
    <!-- Header Component -->
    <LayoutHeader />

    <!-- Main Content -->
    <main>
      <slot />
    </main>

    <!-- Footer Component -->
    <LayoutFooter />
  </div>
</template>

<script setup>
// This layout will be used for all pages automatically
</script>

<style scoped>
/* RTL support for Persian content */
* {
  font-family: 'Vazir', 'Tahoma', sans-serif;
}
</style>