<script setup>
import axios from "axios";
import { onMounted, ref } from "vue";
import VideoPlayer from "@/components/VideoPlayer.vue";

const youtubeData = ref({});
const selectedYTVideo = ref();

const fetchYoutubeData = async () => {
  const url = `https://www.googleapis.com/youtube/v3/search?part=snippet&q=arts&maxResults=50&key=${
    import.meta.env.VITE_API_KEY
  }`;
  try {
    const response = await axios.get(url);

    console.log(response.data.items);
    youtubeData.value = response.data.items
      .filter((filterData) => filterData.snippet.channelTitle !== filterData.snippet.title)
      .sort((a, b) => new Date(b.snippet.publishedAt) - new Date(a.snippet.publishedAt))
      .map((apiData) => {
        let title = apiData.snippet.title;
        const titleMaxLength = 25;
        if (apiData.snippet.title.length > titleMaxLength) {
          title = apiData.snippet.title.substring(0, titleMaxLength - 3) + "...";
        }

        return {
          videoId: apiData.id.videoId,
          thumbnail: apiData.snippet.thumbnails.high.url,
          title,
          fullTitle: apiData.snippet.title,
          channelTitle: apiData.snippet.channelTitle,
          publishedAt: new Date(apiData.snippet.publishedAt).toLocaleDateString("en-US", {
            month: "short",
            day: "numeric",
            year: "numeric",
          }),
        };
      });
  } catch (error) {
    youtubeData.value = {};
    console.error("Error fetching video titles:", error);
  }
};
const showModal = ref(false);

const modalToggle = (value, indexOfYt) => {
  showModal.value = value;
  selectedYTVideo.value = youtubeData.value[indexOfYt];
};

onMounted(fetchYoutubeData);
</script>

<template>
  <div class="main-container flex flex-row justify-center items-center flex-wrap">
    <div v-for="(data, index) in youtubeData" :key="index">
      <!-- <a
        v-if="data.thumbnail"
        :href="`https://www.youtube.com/watch?v=${data.videoId}`"
        target="_blank"
        class="relative group thumbBox rounded-lg m-3 flex flex-col"
      > -->
      <button
        @click="modalToggle(true, index)"
        class="relative group thumbBox rounded-lg m-3 flex flex-col"
      >
        <div class="overflow-hidden rounded-lg">
          <img
            :src="data.thumbnail"
            alt="Thumbnail"
            class="transition-transform duration-200 ease-in-out transform group-hover:scale-110"
          />
        </div>
        <p class="poppins-font-semibold text-gray-700 mt-2">{{ data.title }}</p>
        <p class="poppins-font-regular text-gray-400 text-sm">{{ data.publishedAt }}</p>
        <span
          class="tooltip absolute bottom-0 p-3 bg-white poppins-font-semibold text-gray-700 z-30 opacity-0 group-hover:opacity-100 transition-opacity duration-300 ease-in-out text-sm"
        >
          {{ data.fullTitle }}
        </span>
      </button>

      <!-- </a> -->
    </div>
  </div>

  <div>
    <VideoPlayer
      :showModal="showModal"
      :modalToggle="modalToggle"
      :selectedYTVideo="selectedYTVideo"
    />
  </div>
</template>

<style scoped>
.main-container {
  width: 100%;
  /* height: 100vh; */
  /* overflow-y: scroll; */
}

.thumbBox {
  width: 250px;
}
</style>
