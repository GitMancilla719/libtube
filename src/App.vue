<script setup>
import VideoList from "@/components/VideoList.vue";
import SideBar from "@/components/SideBar.vue";
import NavBar from "@/components/NavBar.vue";
</script>

<template>
  <div>
    <NavBar />
  </div>

  <div class="flex">
    <div class="h-screen leftPanel">
      <SideBar />
    </div>

    <div class="no-scrollbar h-screen rightPanel overflow-y-scroll">
      <div class="py-10 mt-12 px-7 text-center flex flex-col justify-start items-center">
        <h2 class="poppins-font-semibold text-[#6545ba] mt-2 text-3xl md:text-4xl lg:text-4xl">
          The Best Art Inspiration, Tutorials, and More.
        </h2>
        <p class="poppins-font-regular text-gray-500 mt-2 md:w-full lg:w-3/4">
          Seeking artistic inspiration? Look no further. Our curated collection features the finest
          art videos, showcasing incredible creativity, techniques, and styles. Immerse yourself in
          a handpicked selection of real art videos, each chosen for their exceptional artistic
          quality.
        </p>
      </div>

      <VideoList />
    </div>
  </div>
</template>

<style scoped>
.leftPanel {
  width: 20%;
}

.rightPanel {
  width: 80%;
}

.no-scrollbar::-webkit-scrollbar {
  display: none;
}

.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
