<script setup>
import numeral from 'numeral'

const video = ref(null);
onMounted(() => {
  video.value.play();
});
</script>

<template>
  <div class="flex border-b py-6" id="MainPost">
    <div class="cursor-pointer">
      <TheAvatar class="w-[60px] h-[60px]" />
    </div>
    <div class="pl-3 w-full px-4">
      <div class="flex items-center justify-between pb-0.5">
        <button>
          <span class="font-bold hover:underline cursor-pointer">
            username
          </span>
          <span class="text-base pl-1 cursor-pointer"> full name </span>
        </button>
        <button
          class="border text-[15px] px-[21px] py-0.5 border-primary text-primary hover:bg-[#ffeef2] font-semibold rounded-md"
        >
          Follow
        </button>
      </div>

      <div
        class="text-[15px] pb-0.5 break-words md:max-w-[400px] max-w-[300px]"
      >
        <TheHashtag tags="#fun #cool #SuperAwesome" />
        <span>This is some random text for testing </span>
      </div>
      <div class="text-[14px] pb-0.5 flex items-center">
        <Icon name="mdi:music" size="17" />
        <div class="px-1">original sound - Glory</div>
        <Icon name="mdi:heart" size="20" />
      </div>

      <div class="mt-2.5 flex">
        <div
          class="relative min-h-[480px] max-h-[580px] max-w-[260px] flex items-center bg-black rounded-xl cursor-pointer"
        >
          <video
            src="/videos/SnapSave.io-لا تجلس في مكان تُظلم فيه !.mp4"
            ref="video"
            loop
            muted
            class="rounded-xl object-cover mx-auto h-full"
          />
        </div>

        <div class="relative mr-[75px]">
          <div class="absolute bottom-0 pl-2">
            
            <div class="pb-4 text-center">
              <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                <Icon name="mdi:heart" size="25" />
              </button>
              <span class="text-xs text-gray-800 font-semibold">{{ numeral(37000).format('+0a') }}</span>
            </div>

            <div class="pb-4 text-center">
              <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                <Icon name="iconamoon:comment-dots-fill" size="25" />
              </button>
              <span class="text-xs text-gray-800 font-semibold">{{ numeral(37000).format('+0a') }}</span>
            </div>

            <div class="pb-4 text-center">
              <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                <Icon name="ri:share-forward-fill" size="25" />
              </button>
              <span class="text-xs text-gray-800 font-semibold">{{ numeral(37000).format('+0a') }}</span>
            </div>

          </div>
        </div>

      </div>
    </div>
  </div>
</template>
