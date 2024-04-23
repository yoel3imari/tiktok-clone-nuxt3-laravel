<script setup>
const props = defineProps(["customClass"]);
let { customClass } = toRefs(props);
</script>

<template>
  <!-- <img
    src="https://picsum.photos/id/30/300/320"
    class="rounded-full"
    :class="customClass"
    alt="avatar"
  /> -->
  <span
    class="bg-[url('https://picsum.photos/id/30/300/320')] bg-primary bg-cover bg-center block rounded-full"
    :class="customClass"
  />
</template>
