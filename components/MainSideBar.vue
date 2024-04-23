<script setup>
const route = useRoute();
</script>

<template>
  <div
    id="MainSideNav"
    class="fixed z-20 bg-white pt-[70px] h-full lg:border-r-0 border-r w-[75px] overflow-auto"
    :class="route.fullPath === '/' ? 'lg:w-[310px]' : 'lg:w-[220px]'"
  >
    <div class="lg:w-full w-[55px] mx-auto">
      <NuxtLink>
        <MenuItem
          icon="mdi:home"
          iconString="For You"
          colorString="#f02c56"
          sizeString="30"
        />
      </NuxtLink>
      <MenuItem
        iconString="Following"
        icon="ci:group"
        colorString="#000"
        sizeString="27"
      />
      <MenuItem
        iconString="LIVE"
        colorString="#000"
        icon="ri:live-line"
        sizeString="27"
      />

      <div class="border-b lg:ml-2 mt-2"></div>

      <div
        class="lg:block hidden text-xs text-gray-600 font-semibold pt-4 pb-2 px-2"
      >
        Suggested accounts
      </div>

      <div class="lg:hidden block pt-3"></div>

      <div class="cursor-pointer">
        <SuggestedAccountItem />
      </div>

      <button class="lg:block hidden text-primary pt-1.5 pl-2 text-[13px]">
        See all
      </button>

      <div class="border-b lg:ml-2 mt-2"></div>

      <div
        class="lg:block hidden text-xs text-gray-600 font-semibold pt-4 pb-2 px-2"
      >
        Following accounts
      </div>

      <div class="lg:hidden block pt-3"></div>

      <div class="cursor-pointer">
        <SuggestedAccountItem />
      </div>

      <button class="lg:block hidden text-primary pt-1.5 pl-2 text-[13px]">
        See more
      </button>

      <div class="lg:block hidden border-b lg:ml-2 mt-2"></div>

      <div class="lg:block hidden text-[11px] text-gray-500">
        <div class="pt-4 px-2 capitalize">
          About Newsroom TikTok Shop Contact Careers ByteDance
        </div>
        <div class="pt-4 px-2 capitalize">
          TikTok for Good Advertise Developers Transparency TikTok Rewards
          TikTok Browse TikTok
        </div>
        <div class="pt-4 px-2 capitalize">
          Help Safety terms privacy creator portal community guilines
        </div>
        <div class="pt-4 px-2 capitalize flex items-center">
          <Icon name="uil:copyright" size="12" class="" />2023 tiktok
        </div>
      </div>
    </div>
  </div>
</template>
