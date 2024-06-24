<template>
  <v-container>
    <v-row>
      <v-col cols="8" lg="8" sm="8" xs="12" md="12">
        <v-card variant="outlined" v-if="url !== '' && url !== undefined">
          <v-img
            :src="`/resources/${narrative}/${url}`"
            class="bg-grey-lighten-2"
          ></v-img>
          <v-card-actions>
            <v-btn @click="toReturn">
              Regresar a listado de {{ narrative }}
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <!--v-col cols="4" lg="4" sm="4" xs="12" md="12">
        <v-card
          variant="outlined"
          :loading="false"
          title="Ciberbullying"
          subtitle="Décalogo para una victima de ciberbullying"
          text="Es un compornamiento agresivo, intencional y repetido que se produce entre escolares. Implica un desequilibrio de poder o fuerza entre el agresor y la víctima."
        >
          <v-card-actions>
            <v-btn :to="`/${narrative}/${format}/`">Regresar</v-btn>
          </v-card-actions>
        </v-card>
      </v-col-->
    </v-row>
  </v-container>
</template>
<script setup>
const router = useRouter();
const route = useRoute();
const { narrative, format, id } = route.params;
const url = ref("");

const toReturn = () => {
  router.push(`/${narrative}/${format}`);
};

if (route.query.url) {
  url.value = route.query.url;
}
</script>
