<script setup>
import { ref, watch, defineProps } from "vue";
import LiteYouTubeEmbed from "vue-lite-youtube-embed";
import "vue-lite-youtube-embed/style.css";

const props = defineProps({
  showModal: Boolean,
  modalToggle: Function,
  selectedYTVideo: Object,
});

const showModal = ref(false);

function closeModal() {
  showModal.value = false;
  props.modalToggle(false, []);
}

watch(
  () => props.showModal,
  (newValue, oldValue) => {
    showModal.value = newValue;
  }
);
</script>

<template>
  <div
    v-if="showModal"
    class="fixed inset-0 bg-gray-500 bg-opacity-50 overflow-auto px-4 py-6 sm:px-0 z-50"
  >
    <div class="relative mx-auto rounded-sm shadow-xl bg-white max-w-xl">
      <div class="p-4">
        <LiteYouTubeEmbed :id="props.selectedYTVideo.videoId" />

        <p class="poppins-font-semibold text-lg text-gray-700 mt-2">
          {{ props.selectedYTVideo.fullTitle }}
        </p>
        <p class="poppins-font-regular text-gray-400 text-sm">
          {{ props.selectedYTVideo.publishedAt }}
        </p>

        <button
          @click="closeModal"
          class="w-full mt-4 px-4 py-2 text-sm font-medium bg-red-50 text-red-500 rounded-sm hover:bg-red-200"
        >
          Close
        </button>
      </div>
    </div>
  </div>
</template>
