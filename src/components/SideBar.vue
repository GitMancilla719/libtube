<script setup>
const artCategories = [
  "Painting",
  "Sculpture",
  "Printmaking",
  "Drawing",
  "Architecture",
  "Photography",
  "Cinema",
  "Graphic design",
  "Industrial design",
  "Fashion design",
  "Interior design",
  "Performance art",
  "Video art",
  "Installation art",
  "Land art",
  "New media art",
];
</script>

<template>
  <div class="h-screen flex justify-center items-center bg-gray-100">
    <div class="catContainer p-5 bg-white rounded-lg flex flex-col justify-center">
      <a
        href="#"
        v-for="category in artCategories"
        :key="category"
        class="poppins-font-regular m-1 text-gray-600 hover:text-[#6545ba] hover:font-semibold"
      >
        {{ category }}
      </a>
    </div>
  </div>
</template>

<style scoped>
.catContainer {
  width: 210px;
  height: 85%;
}
</style>
