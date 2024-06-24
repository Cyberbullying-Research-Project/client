<template>
  <div>
    <v-card :title="`Infografías de ${narrative}`" variant="outlined">
      <v-card-item>
        <v-row>
          <v-col cols="12">
            <v-card
              variant="tonal"
              color="#303F9F"
              v-for="(infographic, i) in infographics"
              :key="i"
            >
              <v-img
                class="bg-grey-lighten-2"
                height="125"
                :src="`/resources/${narrative}/${infographic.src}`"
                cover
              ></v-img>
              <v-card-actions class="text-h6">
                <v-spacer></v-spacer>
                <v-btn icon color="green" @click="previewInfographic(i)">
                  <v-icon size="x-large">mdi-eye</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-card-item>
      <v-row>
        <v-col cols="12" class="pa-0 mx-lg-auto">
          <CommonCounter :count="infographics.length" />
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

const previewInfographic = (i) => {
  router.push(`/${narrative}/${format}/view?url=${infographics.value[i].src}`);
};

const categories = ref({
  ciberbullying: [
    {
      src: "infographic_ciberbullying.png",
    },
  ],
  grooming: [{ src: "infographic_grooming.png" }],
  sexting: [
    {
      src: "infographic_sexting.png",
    },
  ],
});

const infographics = ref(categories.value[narrative]);
</script>
