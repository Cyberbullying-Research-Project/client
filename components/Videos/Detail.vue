<template>
  <v-container>
    <v-card v-if="url !== '' && url !== undefined" variant="text">
      <v-card-actions>
        <v-btn @click="toReturn">
          Regresar a listado de videos de {{ narrative }}
        </v-btn>
      </v-card-actions>
      <v-row>
        <v-col cols="12">
          <v-sheet
            elevation="12"
            rounded="lg"
            width="100%"
            class="pa-4 text-center mx-auto"
          >
            <h2 class="text-h5 mb-6">Video en {{ narrative }}</h2>

            <div class="video-container">
              <iframe
                ref="videoFrame"
                :src="`${url}?start=1`"
                title="YouTube video player"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                allowfullscreen
              ></iframe>
              <v-divider class="mb-4"></v-divider>
              <div class="video-controls">
                <v-btn
                  @click="fullscreenVideo"
                  class="mx-2"
                  color="primary"
                  rounded
                  variant="outlined"
                >
                  <v-icon>mdi-fit-to-screen</v-icon>
                </v-btn>
              </div>
            </div>
          </v-sheet>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script setup>
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();
const { narrative, format } = route.params;
const videoFrame = ref(null);
const isYouTubeVideo = ref(false);
const url = ref("");

if (route.query.url) {
  url.value = route.query.url;
}

const toReturn = () => {
  router.push(`/${narrative}/${format}`);
};

if (route.query.url && route.query.url.includes("youtube.com")) {
  isYouTubeVideo.value = true;
}

const expandVideo = () => {
  if (videoFrame.value) {
    videoFrame.value.style.width = "100%";
    videoFrame.value.style.height = "auto";
  }
};

const fullscreenVideo = () => {
  if (videoFrame.value) {
    if (videoFrame.value.requestFullscreen) {
      videoFrame.value.requestFullscreen();
    } else if (videoFrame.value.mozRequestFullScreen) {
      videoFrame.value.mozRequestFullScreen();
    } else if (videoFrame.value.webkitRequestFullscreen) {
      videoFrame.value.webkitRequestFullscreen();
    }
  }
};
</script>

<style scoped>
.video-container {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* 16:9 aspect ratio */
  height: 0;
  overflow: hidden;
}

.video-container iframe,
.video-container video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.video-controls {
  margin-top: 10px;
}
</style>
