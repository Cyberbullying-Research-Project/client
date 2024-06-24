<template>
  <v-container>
    <v-card color="#000" variant="outlined">
      <v-card-title class="text-center justify-center py-6">
        <HomeParalaxCard />
      </v-card-title>

      <v-tabs v-model="tab" bg-color="#AA3939" color="#FFF" grow>
        <v-tab v-for="item in items" :key="item" :value="item">
          {{ item }}
        </v-tab>
      </v-tabs>

      <v-window v-model="tab">
        <v-window-item v-for="item in items" :key="item" :value="item">
          <v-card color="#AA3939" flat>
            <v-container fluid>
              <v-card-text>
                <HomeItemsCard :tabsCards="textTab[item]" :item="item" />
              </v-card-text>
            </v-container>
          </v-card>
        </v-window-item>
      </v-window>
    </v-card>
  </v-container>
</template>

<script setup>
import { ref } from "vue";

const tab = ref("ciberbullying");

const items = ["ciberbullying", "grooming", "sexting"];
const textTab = {
  ciberbullying: {
    inphographic: {
      text: "",
      image:
        "/resources/ciberbullying/iconos-Bimadino-5CyberBulling-Infografia.png",
    },
    podcast: {
      text: "",
      image:
        "/resources/ciberbullying/iconos-Bimadino-6Cyberbulling-Podcast.png",
    },
    video: {
      text: "",
      image: "/resources/ciberbullying/iconos-Bimadino-7CyberbullingVideo.png",
    },
  },
  sexting: {
    inphographic: {
      text: "",
      image: "/resources/sexting/iconos-Bimadino-9-Sexting-Infografia.png",
    },
    podcast: {
      text: "",
      image: "/resources/sexting/iconos-Bimadino-8-Sexting-Podcast.png",
    },
    video: {
      text: "",
      image: "/resources/sexting/iconos-Bimadino-10-SextingVideo.png",
    },
  },
  grooming: {
    inphographic: {
      text: "",
      image: "/resources/grooming/iconos-Bimadino-11-Grooming-Infografia.png",
    },
    podcast: {
      text: "",
      image: "/resources/grooming/iconos-Bimadino-12-Grooming-Podcast.png",
    },
    video: {
      text: "",
      image: "/resources/grooming/iconos-Bimadino-13Grooming-Video.png",
    },
  },
};
</script>

<style scope>
/* Helper classes */
.bg-basil {
  background-color: #fff !important;
}
.text-basil {
  color: #356859 !important;
}
.custom-tab {
  color: #aa3939; /* Color de las pestañas inactivas */
}
.custom-tab-active {
  color: #801515; /* Color de la pestaña activa */
}

.v-tab--selected {
  color: #222222 !important;
  background-color: #ffff !important;
}
</style>
