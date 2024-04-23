<template>
  <div
    class="w-full mt-[80px] mb-[40px] bg-white shadow-lg rounded-md py-6 md:px-10 px-4"
  >
    <div>
      <div class="text-2xl">Upload video</div>
      <div class="text-gray-400 mt-1">Post a video to your account</div>
    </div>
    <div class="mt-8 md:flex gap-6">
      <label
        v-if="!fileDisplay"
        for="fileInput"
        @dragover.prevent="($event) => {}"
        @drop.prevent="onDrop"
        class="md:mx-0 mx-auto mt-4 mb-6 flex flex-col items-center justify-center w-full max-w-[260px] h-[470px] text-center p-3 border-2 border-dashed border-gray-300 rounded-lg hover:bg-gray-100 cursor-pointer"
      >
        <Icon name="majesticons:cloud-upload" size="40" color="#b3b3b1" />
        <div class="mt-4 text-gray-500 text-xl">Select video to upload</div>
        <div class="mt-1.5 text-gray-400 text-base">
          Or drag and drop a file
        </div>
        <div class="mt-12 text-gray-400 text-base">MP4</div>
        <div class="mt-2 text-gray-400 text-base">Up to 30 minutes</div>
        <div class="mt-2 text-gray-400 text-base">Less than 2GB</div>
        <div
          class="px-2 mt-8 py-1.5 text-white text-base w-[80%] bg-primary rounded-sm hover:bg-[#b32944]"
        >
          Select file
        </div>
        <input
          type="file"
          @change="onChange"
          ref="file"
          id="fileInput"
          hidden
          accept=".mp4, .webm, .mkv"
        />
      </label>
      <div
        v-else
        class="md:mx-0 mx-auto mt-4 md:mb-12 mb-16 flex items-center justify-center w-full max-w-[260px] h-[540px] p-3 rounded-2xl cursor-pointer relative"
      >
        <div class="bg-black w-full h-full"></div>
        <img
          src="~/assets/images/mobile-case.png"
          class="absolute z-20 pointer-events-none"
          alt=""
        />

        <video
          :src="fileDisplay"
          ref="video"
          id="fileInput"
          loop
          muted
          class="rounded-xl object-fill mx-auto h-full"
        />

        <div
          class="absolute -bottom-12 flex items-center justify-between z-50 rounded-xl border w-full p-2 border-gray-300"
        >
          <div class="flex items-center truncate">
            <Icon
              name="clarity:success-standard-line"
              size="16"
              class="min-w-[16px]"
            />
            <div class="text-xs pl-1 truncate text-ellipsis">
              {{ fileData.name }}
            </div>
          </div>
          <button
            @click="cleanVideo"
            class="text-xs ml-2 mr-1 font-semibold cursor-pointer"
          >
            Change
          </button>
        </div>
      </div>

      <div class="mt-4 mb-6">
        <div class="flex bg-[#f8f8f8] py-4 px-6">
          <div>
            <Icon class="mr-4" size="20" name="mdi:box-cutter-off" />
          </div>
          <div>
            <div class="font-semibold text-base mb-1.5">
              Divide videos and edit
            </div>
            <div class="font-semibold text-sm text-gray-400">
              You can quickly divide videos into multiple parts, remove
              redundant parts and turn landscape vides into portrait videos
            </div>
          </div>
          <div
            class="flex justify-end max-w-[130px] w-full h-full text-center my-auto"
          >
            <button
              class="px-8 py-1.5 text-white text-base bg-primary rounded-sm"
            >
              Edit
            </button>
          </div>
        </div>
        <div class="mt-5">
          <div class="flex items-center justify-between">
            <div class="mb-1 text-base">Caption</div>
            <div class="text-gray-400 text-xs">0/150</div>
          </div>
          <textarea
            v-model="caption"
            aria-rowcount="5"
            type="text"
            class="w-full line border p-2.5 rounded-md focus:outline-none"
          />
        </div>
        <div class="flex gap-3">
          <button
            @click="onDiscard"
            class="px-10 py-2.5 mt-8 border text-base hover:bg-gray-100 rounded-sm"
          >
            Discard
          </button>
          <button
            class="px-10 py-2.5 mt-8 border text-base bg-primary text-[#f8f8f8] rounded-sm"
          >
            Post
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: "upload-layout",
});

let file = ref(null);
let fileDisplay = ref(null);
let fileData = ref(null);
let errorType = ref(null);
let caption = ref(null);
let error = ref(null);
let isUploading = ref(false);

const onDrop = (e) => {
  errorType.value = "";
  file.value = e.dataTransfer.files[0];
  fileData.value = e.dataTransfer.files[0];

  let extension = file.value.name.substring(
    file.value.name.lastIndexOf(".") + 1
  );

  if (!["mp4", "webm", "mkv"].includes(extension.toLowerCase())) {
    errorType.value = "file";
    return;
  }

  fileDisplay.value = URL.createObjectURL(e.dataTransfer.files[0]);
};

const onChange = () => {
  fileDisplay.value = URL.createObjectURL(file.value.files[0]);
  fileData.value = file.value.files[0];
};

const onDiscard = () => {
  file.value = null;
  fileDisplay.value = null;
  fileData.value = null;
  errorType.value = null;
  caption.value = null;
};
</script>
