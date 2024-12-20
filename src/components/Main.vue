<script setup lang="ts">
import { ref, computed } from "vue";

const techPoint = ref(0);
const faithPoint = ref(0);
const techLevel = computed(() => {
  return pointToLevel(techPoint.value);
});
const faithLevel = computed(() => {
  return pointToLevel(faithPoint.value);
});

const pointToLevel = (point: number): number => {
  return Math.floor(Math.log2(point + 1));
};

const reset = () => {
  techPoint.value = 0;
  faithPoint.value = 0;
};
</script>

<template>
  <div min-width="400px" max-width="800px" class="fill-height d-flex align-center justify-center">
    <v-container>
      <v-layout row>
        <v-col cols="6" class="text-center">
          <v-icon icon="mdi-cog-outline" class="text-h2"></v-icon>
        </v-col>
        <v-col cols="6" class="text-center">
          <v-icon icon="mdi-book-cross" class="text-h2"></v-icon>
        </v-col>
      </v-layout>
      <v-layout row class="d-flex align-center justify-center mb-16">
        <v-col cols="3">
          <VerticalCounter
            :count="techPoint"
            @increment="
              () => {
                if (techPoint < 15) {
                  techPoint++;
                }
              }
            "
            @decrement="
              () => {
                if (techPoint > 0) {
                  techPoint--;
                }
              }
            "
          />
        </v-col>
        <v-col cols="3">
          <div class="text-center">
            <h1 class="text-h2 font-weight-bold">{{ techLevel }}</h1>
          </div>
        </v-col>
        <v-col cols="3">
          <div class="text-center">
            <h1 class="text-h2 font-weight-bold">{{ faithLevel }}</h1>
          </div>
        </v-col>
        <v-col cols="3">
          <VerticalCounter
            :count="faithPoint"
            @increment="
              () => {
                if (faithPoint < 15) {
                  faithPoint++;
                }
              }
            "
            @decrement="
              () => {
                if (faithPoint > 0) {
                  faithPoint--;
                }
              }
            "
          />
        </v-col>
      </v-layout>
      <v-layout row class="d-flex justify-center">
        <v-btn
          block
          color="#f25865"
          size="regular"
          rounded="lg"
          variant="outlined"
          @click="reset()"
          min-height="40px"
        >
          Reset
        </v-btn>
      </v-layout>
    </v-container>
  </div>
</template>
