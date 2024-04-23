<script setup>
const props = defineProps(['user'])
</script>

<template>
  <div
    class="flex items-center hover:bg-gray-100 rounded-md w-full py-1.5 px-2"
  >
    <!-- <img
      src="https://picsum.photos/id/8/300/350"
      alt="avatar"
      width="35"
      height="35"
      class="rounded-full lg:mx-0 mx-auto"
    /> -->
    <TheAvatar class="lg:mx-0 mx-auto w-9 h-9" />
    <div class="lg:pl-2.5 lg:block hidden">
      <div class="flex items-center">
        <div class="font-bold text-[14px]">
          username
        </div>
        <div class="ml-1 rounded-full bg-[#58d5ec] h-[14px] relative">
          <Icon class="relative -top-[7px]" name="teenyicons:tick-small-solid" color="#fff" size="14" /> 
        </div>
      </div>
      <div class="font-light text-[12px] text-gray-600">full name here</div>
    </div>
  </div>
</template>
