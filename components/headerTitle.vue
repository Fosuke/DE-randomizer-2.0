<script setup>
const props = defineProps(["inactiveGame", "modelValue"]);
const emit = defineEmits(["update:modelValue"]);

const dialog = computed({
  get() {
    return props.modelValue;
  },
  set(newValue) {
    emit("update:modelValue", newValue);
  },
});
</script>

<template>
  <v-card-item class="rounded bg-blue-grey-lighten-4">
    <v-row>
      <v-col sm="11" cols="10">
        <v-card-title :class="{ 'text-wrap': inactiveGame }"
          >Randomize Sentinels of the Multiverse: Definitive
          Edition</v-card-title
        >

        <v-card-subtitle>By Fosuke</v-card-subtitle>
      </v-col>
      <v-col cols="1">
        <v-card-actions>
          <v-btn dark icon="mdi-cog" @click="dialog = true"> </v-btn>
        </v-card-actions>
      </v-col>
    </v-row>
  </v-card-item>
</template>