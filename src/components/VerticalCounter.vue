<script setup lang="ts">
import { defineEmits, defineProps } from "vue";

defineProps<{
  count: number;
}>();

const emit = defineEmits(["increment", "decrement"]);

const incr = () => {
  emit("increment", null);
};
const decr = () => {
  emit("decrement", null);
};
</script>

<template>
  <div class="d-flex flex-column justify-center">
    <v-btn
      density="compact"
      size="regular"
      rounded="lg"
      variant="outlined"
      @click="incr()"
      min-height="60px"
    >
      <v-icon icon="mdi-menu-up" class="text-h2 my-n4"></v-icon>
    </v-btn>
    <div class="text-center">
      <h1 class="text-h3 font-weight-bold">{{ count }}</h1>
    </div>
    <v-btn
      density="compact"
      size="regular"
      rounded="lg"
      variant="outlined"
      @click="decr()"
      min-height="60px"
    >
      <v-icon icon="mdi-menu-down" class="text-h2 my-n4"></v-icon>
    </v-btn>
  </div>
</template>
