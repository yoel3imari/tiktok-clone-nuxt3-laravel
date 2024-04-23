<script setup>
const route = useRoute();
</script>

<template>
  <TopNav />
  <div
    class="flex justify-between mx-auto w-full lg:px-2.5 px-0"
    :class="route.fullPath === '/' ? 'max-w-[1140px]' : ''"
  >
    <div>
      <MainSideBar />
    </div>
    <slot />
  </div>
</template>
