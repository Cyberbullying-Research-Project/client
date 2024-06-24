<template>
  <div>
    <v-card :title="`Videos de ${narrative}`" variant="outlined">
      <v-card-item>
        <v-row>
          <v-col cols="12">
            <v-list :items="videos" lines="three" item-props>
              <template v-slot:subtitle="{ subtitle }">
                <div v-html="subtitle"></div>
              </template>

              <template v-slot:append="{ item }">
                <v-list-item-action start>
                  <a
                    class="text-decoration-none"
                    :href="`/${narrative}/videos/watch?url=${item.url}`"
                  >
                    <v-icon icon="mdi-play-circle" size="x-large"></v-icon>
                  </a>
                </v-list-item-action>
              </template>
            </v-list>
          </v-col>
        </v-row>
      </v-card-item>
      <v-row>
        <v-col cols="12" class="pa-0 mx-lg-auto">
          <CommonCounter :count="videos.length" />
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

const toReturn = () => {
  router.push(`/${narrative}`);
};

const previewInfographic = () => {
  router.push(`/${narrative}/${format}/1`);
};

const categories = ref({
  ciberbullying: [
    {
      prependAvatar: "/images/video.png",
      title: "Ciberbulling Concepto",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video pretende explicar el concepto de ciberbulling.`,
      url: `https://www.youtube.com/embed/o9T-v0GePQY?si=J6XnnNmGbe36IH7s`,
    },
    { type: "divider", inset: true },
    {
      prependAvatar: "/images/video.png",
      title: "Ciberbulling experiencia",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video muestra la experiencia de una persona que ha sido víctima de ciberbulling.`,
      url: `https://www.youtube.com/embed/1Hs06zpewoY?si=h347xwwCqmgOw8iv`,
    },
    { type: "divider", inset: true },
    {
      prependAvatar: "/images/video.png",
      title: "Ciberbulling Opinion",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video muestra la opinion de una persona sobre el ciberbulling.`,
      url: `https://www.youtube.com/embed/1ftnJkR6KN4?si=ZpnX44aIuo17UqZx`,
    },
    { type: "divider", inset: true },
  ],
  grooming: [
    {
      prependAvatar: "/images/video.png",
      title: "Grooming Concepto",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video pretende explicar el concepto de grooming.`,
      url: `https://www.youtube.com/embed/Uegv1eJADlA?si=DvM3zQW8vFrxiwAi`,
    },
    { type: "divider", inset: true },
    {
      prependAvatar: "/images/video.png",
      title: "Grooming experiencia",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video muestra la experiencia de una persona que ha sido víctima de grooming.`,
      url: `https://www.youtube.com/embed/HdgDrSGzdUc?si=zU1KuXaiWhM17Rfc`,
    },
  ],
  sexting: [
    {
      prependAvatar: "/images/video.png",
      title: "Sexting experiencia",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video muestra la experiencia de una persona que ha sido víctima de sexting.`,
      url: `https://www.youtube.com/embed/12p_N4DK0Qk?si=Trk7-lb8k8WUHQYp`,
    },
    { type: "divider", inset: true },
    {
      prependAvatar: "/images/video.png",
      title: "Sexting Opinion",
      subtitle: `<span class="text-primary">Anónimo</span> &mdash; El siguiente video muestra la experiencia de una persona que ha sido víctima de sexting.`,
      url: `https://www.youtube.com/embed/jkf4UZJXsOE?si=Y91xIs9pdyOdA7cn`,
    },
    { type: "divider", inset: true },
  ],
});

const videos = categories.value[narrative];
</script>
