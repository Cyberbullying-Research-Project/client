<template>
  <div>
    <v-card :title="`Podcast de ${narrative}`" variant="outlined">
      <v-card-item>
        <v-row>
          <v-col cols="12">
            <v-list :items="podcasts" lines="three" item-props>
              <template v-slot:subtitle="{ subtitle }">
                <div v-html="subtitle"></div>
              </template>
              <template v-slot:append="{ item }">
                <v-btn
                  color="green"
                  variant="text"
                  @click="previewPodcast(item.url)"
                >
                  <v-icon size="x-large">mdi-headphones</v-icon>
                </v-btn>
              </template>
            </v-list>
          </v-col>
        </v-row>
      </v-card-item>
      <v-row>
        <v-col cols="12" class="pa-0 mx-lg-auto">
          <CommonCounter :count="podcasts.length" />
        </v-col>
      </v-row>
      <v-card-actions>
        <v-btn @click="toReturn"> Regresar a {{ narrative }} </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>
<script setup>
const router = useRouter();
const route = useRoute();

const { narrative, format } = route.params;

const toReturn = (url) => {
  router.push(`/${narrative}`);
};

const previewPodcast = (url) => {
  router.push(`/${narrative}/${format}/listen?url=${url}`);
};

const categories = ref({
  ciberbullying: [
    {
      prependAvatar: "/images/podcast.png",
      title: "Podcast mezcla",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente testimonio es una mezcla de varios testimonios de personas que han vivido situaciones de acoso escolar.`,
      url: "podcast_ciberbullying_mezcla.wav",
    },
    { type: "divider", inset: true },
  ],
  grooming: [
    {
      prependAvatar: "/images/podcast.png",
      title: "Podcast mezcla",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente testimonio es una mezcla de varios testimonios de personas que han vivido situaciones de acoso escolar.`,
      url: "podcast_grooming_mezcla.wav",
    },
    { type: "divider", inset: true },
  ],
  sexting: [
    {
      prependAvatar: "/images/podcast.png",
      title: "Podcast mezcla",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente testimonio es una mezcla de varios testimonios de personas que han vivido situaciones de acoso escolar.`,
      url: "podcast_sexting_mezcla.wav",
    },
    { type: "divider", inset: true },
  ],
});

const podcasts = ref(categories.value[narrative]);
</script>
