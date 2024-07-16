<script setup>
import axios from "axios";
import { ref } from "vue";

const youtubeData = ref({});

const fetchYoutubeData = async () => {
  const apiKey = "AIzaSyBPy_-cpvlW3q8T2J9_ihATyu8UL_52BV0";
  const url = `https://www.googleapis.com/youtube/v3/search?part=snippet&q=artss&maxResults=50&key=${apiKey}`;
  try {
    const response = await axios.get(url);
    youtubeData.value = response.data.items
      .filter((filterData) => filterData.snippet.channelTitle !== filterData.snippet.title)
      .map((apiData) => {
        let title = apiData.snippet.title;
        const titleMaxLength = 25;
        if (apiData.snippet.title.length > titleMaxLength) {
          title = apiData.snippet.title.substring(0, titleMaxLength - 3) + "...";
        }

        return {
          thumbnail: apiData.snippet.thumbnails.high.url,
          title,
          channelTitle: apiData.snippet.channelTitle,
          publishedAt: new Date(apiData.snippet.publishedAt).toLocaleString(),
        };
      });
  } catch (error) {
    youtubeData.value = {};
    console.error("Error fetching video titles:", error);
  }
};

fetchYoutubeData();
</script>

<template>
  <pre>
    {{ youtubeData }}
  </pre>
  <div class="flex flex-row justify-center items-center flex-wrap">
    <div v-for="(data, index) in youtubeData" :key="index">
      <div v-if="data.thumbnail" class="thumbBox rounded-lg m-1 flex flex-col">
        <!-- <img :src="data.thumbnail" alt="Thumbnail" class="object-cover w-full h-full" /> -->
        <div class="overflow-hidden rounded-lg">
          <img
            :src="data.thumbnail"
            alt="Thumbnail"
            class="transition-transform duration-200 ease-in-out transform hover:scale-110"
          />
        </div>
        <p>{{ data.title }}</p>
        <p>{{ data.publishedAt }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.thumbBox {
  /* height: 300px; */
  width: 250px;
}
</style>
