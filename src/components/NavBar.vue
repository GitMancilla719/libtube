<template>
  <nav class="sticky bg-white shadow-sm poppins-font-regular">
    <div class="container mx-auto px-4 flex items-center justify-between h-16">
      <div class="flex items-center">
        <!-- <img src="@/assets/vue.svg" alt="Your Brand" class="h-8 w-8 mr-2" /> -->
        <p class="poppins-font-bold text-xl">ART<span class="text-[#6545ba]">UBE</span></p>
      </div>

      <ul class="flex items-center space-x-4 text-sm">
        <li class="relative group">
          <a href="#" class="group-hover:text-gray-700 px-3 py-2 rounded hover:bg-gray-100">
            Pricing
          </a>
          <ul class="absolute hidden group-hover:block w-40 rounded-md shadow-xl bg-white mt-1">
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Fish</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Chicken</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Cow</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Elephant</a></li>
          </ul>
        </li>
        <li class="relative group">
          <a href="#" class="group-hover:text-gray-700 px-3 py-2 rounded hover:bg-gray-100"
            >About</a
          >
          <ul class="absolute hidden group-hover:block w-40 rounded-md shadow-xl bg-white mt-1">
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Fish</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Chicken</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Cow</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Elephant</a></li>
          </ul>
        </li>
        <li class="relative group">
          <a href="#" class="group-hover:text-gray-700 px-3 py-2 rounded hover:bg-gray-100"
            >Products</a
          >
          <ul class="absolute hidden group-hover:block w-40 rounded-md shadow-xl bg-white mt-1">
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Fish</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Chicken</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Cow</a></li>
            <li><a href="#" class="block px-4 py-2 hover:bg-gray-100">Elephant</a></li>
          </ul>
        </li>
        <li><a href="#" class="text-gray-700 px-3 py-2 rounded hover:bg-gray-100">Contact</a></li>
      </ul>
    </div>
  </nav>
</template>

<script setup></script>

<style scoped>
/* Add any Tailwind CSS customizations here */
</style>
