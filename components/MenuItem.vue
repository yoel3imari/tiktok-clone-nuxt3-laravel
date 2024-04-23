<script setup>
const props = defineProps(["icon", "iconString", "colorString", "sizeString"]);
const { icon, iconString, sizeString, colorString } = toRefs(props);
</script>

<template>
  <div class="w-full flex items-center p-2.5 rounded-md cursor-pointer hover:bg-gray-100">
    <div class="flex items-center lg:mx-0 mx-auto">
      <Icon :name="icon" :color="colorString" :size="sizeString" />
      <span
        :class="`text-[${colorString}]`"
        class="lg:block hidden pl-[9px] mt-0.5 font-semibold text-[17px]"
      >
        {{ iconString }}
      </span>
    </div>
  </div>
</template>
