<template>
  <v-card color="#AA3939" variant="tonal">
    <div class="d-flex flex-no-wrap justify-space-between">
      <div>
        <v-card-title class="text-h5"> {{ narrative.title }} </v-card-title>

        <v-card-subtitle>{{ narrative.body }}</v-card-subtitle>
        <v-list-item class="w-100">
          <v-list-item-subtitle
            >Estado: <v-icon> mdi-eye </v-icon>
            {{ narrative.status }}</v-list-item-subtitle
          >
          <v-list-item-subtitle
            >Creado: <v-icon> mdi-calendar-month </v-icon>
            {{ narrative.created_at }}</v-list-item-subtitle
          >
        </v-list-item>

        <v-card-text>
          <v-btn
            class="me-2 text-none"
            :prepend-icon="typeToIcon[link]"
            variant="flat"
            v-for="link in links"
            :key="link"
            :text="link"
            :to="`/${narrativeLink}/${link}`"
          >
            {{ link }}
          </v-btn>
        </v-card-text>
      </div>
      <v-avatar class="ma-3" size="125" rounded="0">
        <v-img :src="`/resources/icons/${narrativeLink}.png`"></v-img>
      </v-avatar>
    </div>
  </v-card>
</template>
<script setup>
import Inphographics from "~/layouts/inphographics.vue";

// const { narrativeType } = defineProps(['narrativeType']);
const route = useRoute();
const { narrative: narrativeLink } = route.params;

const typeToIcon = {
  inphographics: "mdi-presentation",
  videos: "mdi-video",
  podcasts: "mdi-podcast",
};

const links = ["inphographics", "podcasts", "videos"];

const narrative = {
  id: 1,
  title: narrativeLink,
  body: "",
  user_id: 1,
  status: "published",
  created_at: "2021-09-01",
  category: 1,
};
</script>
