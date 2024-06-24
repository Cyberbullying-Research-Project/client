<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="8">
        <v-container class="max-width">
          <v-pagination
            v-model="page"
            class="my-4"
            :length="count"
          ></v-pagination>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  count: {
    type: Number,
    default: 0,
  },
});

const page = ref(1);
</script>
